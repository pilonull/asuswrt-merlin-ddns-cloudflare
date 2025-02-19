# Asuswrt-Merlin DDNS for CloudFlare

This is a custom shell script for Asuswrt-Merlin router firmware to update DDNS via CloudFlare.

## Setup

1. Add an `A record` in [CloudFlare](https://www.cloudflare.com/) for your domain. IP for the record can be anything since the script will overwrite it later anyway.

1. Download [ddns-start](ddns-start) script and modify the following variables with your own settings:

    `APITOKEN` is your API Token generated from the [User Profile 'API Tokens' page](https://dash.cloudflare.com/profile/api-tokens). I recommend creating a token with minimal access to limit exposure:

    **Permission**: Zone | DNS | Edit  
    **Zone Resources**: Include | Specific Zone | \<your zone\>

    `ZONEID` is your Zone ID, hex16 string

    `RECORDNAME` is your DNS record name, e.g. sub.example.com

    `RECORDTTL` is the TTL for the record in seconds, defaults to auto

1. SSH to your router and place `ddns-start` under `/jffs/scripts/`

1. Make sure it's executable `chmod +x /jffs/scripts/ddns-start`

1. Log into the router web UI

    1. Go to `Advanced Settings` > `WAN` > `DDNS`
    1. Set `Server` to `Custom`
    1. Click the `Apply` button

## References

- <https://github.com/RMerl/asuswrt-merlin/wiki/Custom-DDNS>
- <https://github.com/RMerl/asuswrt-merlin/wiki/User-scripts>
