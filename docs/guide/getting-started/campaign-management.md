---
title: 'Campaign Management'
sidebar_position: 2
---

# Campaign Management on the Usher Platform

## Introduction

Welcome to the Campaign Management section, where we'll guide you through the process of setting up and managing campaigns on the Usher platform. Effective campaign management is crucial to maximizing the potential of your partner programs. By the end of this guide, you'll be equipped with the know-how to create and manage campaigns effectively on Usher.

## Creating and Configuring Campaigns

### Understanding the Campaign Object

Before diving into campaign creation, it's essential to understand the Campaign Object, which consists of immutable campaign terms, mutable campaign details, and the brand/advertiser profile. Immutable terms define the core structure of your campaign, while mutable details and profiles allow for customization and flexibility.

- Campaign Object Example

    ```json
    {
        "id": "ida4Pebl2uULdI_rN8waEw65mVH9uIFTY1JyeZt1PBM",
        "chain": "arweave",
        "owner": "ksFTLgrwQGtNrhRz6MWyd3a4lvK1Oh-QF1HYcEeeFVk",
        "events": [
          {
            "strategy": "flat",
            "rate": 0.1,
            "nativeLimit": 250000,
            "perCommit": 1,
            "description": "files are uploaded"
          }
        ],
        "reward": {
          "name": "Arweave",
          "ticker": "AR",
          "type": "token",
          "limit": 3000
        },
        "conflict_strategy": "PASSTHROUGH",
        "details": {
          "destination_url": "https://app.ardrive.io/#/sign-in?ref=usher",
          "name": "ArDrive Referral Program",
          "description": "Refer users to ArDrive and earn when files are uploaded.",
          "image": "https://ardrive.io/wp-content/uploads/2021/07/Gallery-Angle-PS3000-scaled.jpg",
          "external_link": "https://ardrive.io/"
        },
        "advertiser": {
          "name": "ArDrive",
          "icon": "https://ardrive.io/wp-content/uploads/2021/06/AD-LOGO-PS1600-210x79.png",
          "description": "Upload files forever!",
          "external_link": "https://ardrive.io/",
          "twitter": "https://twitter.com/ardriveapp"
        },
        "disable_verification": false,
        "unlisted": false,
        "whitelist": null
    }
    ```

- Campaign Object Properties


    | Object Property Name/Key | Type | Description | Required |
    | --- | --- | --- | --- |
    | id | string | The identifier of the Campaign. This can be an ID within a Smart Contract or an Blockchain Transaction Address, depending on the chain | true |
    | chain | string | The blockchain identifer. ie. arweave , ethereum, polygon | true |
    | owner | string | The Wallet Address of the Brand/Advertiser | false |
    | events | array | An array of Conversion Events. These Events represent points throughout the Referred User journey at which Conversions are Tracked | false |
    | events[].strategy | string | flat or percentage reward strategy for the event | false |
    | events[].rate | float | Reward rate for the event. For the flat strategy, this rate is flat amount of tokens rewarded to partners.For the percentage strategy, this rate is a multiplier, multiplied by the metadata.amount submitted in the Conversion Parameter | false |
    | events[].nativeLimit | integer | An arbitrary value that limits the conversions that can be processed for this given event for the referred/native user.Where a Conversion.nativeId is provided, rather than restricting conversions to 1 per referred/native user, the Referred User can continue triggering conversions until the sum of  all Conversion.commit values meets this nativeLimit | false |
    | events[].perCommit | integer | If no reward perCommit is defined, the behaviour is standard (ie. X reward rate per Conversion).Otherwise, the reward amount can be relative to the Conversion.commit value, such that reward = rate * (commit / perCommit) | false |
    | events[].description | string | A description for when the event will trigger.The word "when" is prepended to this description in the Usher Partner App UI | false |
    | http://reward.name/ | string | The name of the rewarded http://token.ie/. "Ether", "Arweave", "My Cool NFT" | false |
    | reward.ticker | string | The ticker for the rewarded http://token.ie/. "ETH", "AR", "MYCNFT" | false |
    | reward.type | string | The type of the token rewared to Partners.This is an enumerator with values: token, nft, or pst | false |
    | reward.limit | integer | A limit on the rewards for the entire campaign. When the amount of claimed rewards reaches this limit, the Campaign is considered complete. | false |
    | conflict_strategy | string | PASSTHROUGH or OVERWRITEDetermines how the referral should behave when two Partners refer the same user prior to a tracked conversion.PASSTHROUGH is default, and ensures that the first Invite Link used takes precedence.OVERWRITE is optional and ensures that the last Invite Link used takes precedence. | false |
    | details.destination_url | string | The URL that Campaign Partners will redirect users to. | false |
    | http://details.name/ | string | Name for the Campaign to be recognisable by Partners | false |
    | details.description | string | A description for the Campaign detailing when and how users are converted once the destination_url is reached | false |
    | details.image | string | A hosted image URL to further enhance recognisability of the Campaign | false |
    | details.external_link | string | A URL Partners can visit to receive more information about the Campaign. Can be a landing page promoting the partnership program | false |
    | http://advertiser.name/ | string | Name of the Advertiser | false |
    | advertiser.icon | string | A hosted image URL of the Advertiser's Brand Icon | false |
    | advertiser.description | string | A description of the Advertiser and their related services or propositions | false |
    | advertiser.external_link | string | A URL that Partners can visit to learn more about the Advertiser | false |
    | advertiser.twitter | string | A Twitter URL that Partners can visit to learn more and get updates from the Advertiser | false |
    | disable_verification | boolean | If true, Personhood Verification will NOT be required for Partners to start referring users and earning rewards.Personhood Verification is generally recommended to be active for Campaigns.Learn more on whether your Campaign should include this security measure. | false |
    | unlisted | boolean | Determines whether the Campaign will show on the Usher Explore Page.Partnership Programs that wish to remain private, and/or include a Whitelist of Partners can opt to set this to true | false |
    | whitelist.partners | string[] | An array of Partner http://identifiers.by/ default, Campaigns will not include the Whitelist feature. | false |
    | whitelist.external_link | string | A URL where a Form or other form of data collection is hosted. Partners can use this URL to submit their application to participate in the Partner program. | false |

### Using the Usher Programs CLI or the Usher Onboarding Form

If you're comfortable working with the Terminal and NPM, you can use the [Usher Programs CLI](https://github.com/usherlabs/programs/tree/main/packages/cli) to create campaigns.

However, if you prefer a more guided approach, the Usher team can provide you with a personalized demo and campaign configuration proposal. Fill out the Usher Onboarding Form to express your interest and get started. We're here to help you every step of the way!

Check out this video tutorial demonstrating how to start a campaign and providing additional insights.

[https://www.loom.com/share/d6e631a5528b488384086f520224732d](https://www.loom.com/share/d6e631a5528b488384086f520224732d)

### Configuring Campaign Settings

When setting up a campaign, consider the following:

- Choose the right reward structure: Determine your campaign's most suitable reward type, rate, and limit based on your objectives.
- Set up conversion events: Define the events that trigger rewards, such as registrations or staking.
- Define campaign limits: Establish limits for rewards and conversions to manage your budget effectively.
- Customize campaign details and brand/advertiser profile: Provide information like names, descriptions, images, and external links to make your campaign stand out.

## Managing Campaigns Effectively

### Monitoring Campaign Performance — *Coming soon*

Keep track of your campaign's progress using the Usher platform's built-in metrics. Assess conversions, rewards, and the effectiveness of referral channels to make data-driven decisions for your campaign.

### Modifying Campaigns

Update mutable campaign details and adjust settings based on performance. This flexibility enables you to optimize your campaign for better results.

### Troubleshooting and Support

Address common issues using our troubleshooting guide and seek help from the [Usher Discord Server](https://go.usher.so/discord) for support and community engagement. Otherwise, create a new issue directly within the relevant GitHub repository.

## Conclusion

Now you have a solid understanding of the campaign management process on the Usher platform. Don't hesitate to explore and experiment with different campaign settings to find the perfect fit for your objectives. Remember, the Usher community is always here to help and support you in your journey.