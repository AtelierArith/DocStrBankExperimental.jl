Discordチャンネル。詳細は[こちら](https://discordapp.com/developers/docs/resources/channel#channel-object)を参照してください。

注: `Channel`という名前はすでに使用されているため、プレフィックスがあります。

## Fields

```
id                    :: Snowflake
type                  :: Optional{Int}
guild_id              :: Optional{Snowflake}
position              :: Optional{Int}
permission_overwrites :: Optional{Vector{Ekztazy.Overwrite}}
name                  :: Optional{String}
topic                 :: OptionalNullable{String}
nsfw                  :: Optional{Bool}
last_message_id       :: OptionalNullable{Snowflake}
bitrate               :: Optional{Int}
user_limit            :: Optional{Int}
rate_limit_per_user   :: Optional{Int}
recipients            :: Optional{Vector{Ekztazy.User}}
icon                  :: OptionalNullable{String}
owner_id              :: Optional{Snowflake}
application_id        :: Optional{Snowflake}
parent_id             :: OptionalNullable{Snowflake}
last_pin_timestamp    :: OptionalNullable{DateTime}
```
