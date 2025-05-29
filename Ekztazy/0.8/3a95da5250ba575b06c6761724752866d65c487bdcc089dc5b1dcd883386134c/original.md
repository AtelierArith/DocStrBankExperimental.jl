Discordのギルド（サーバー）。詳細は[こちら](https://discordapp.com/developers/docs/resources/guild#guild-object)を参照してください。

## Fields

```
id                            :: Snowflake
name                          :: String
icon                          :: Nullable{String}
splash                        :: OptionalNullable{String}
owner                         :: Optional{Bool}
owner_id                      :: Optional{Snowflake}
permissions                   :: Optional{String}
region                        :: Optional{String}
afk_channel_id                :: OptionalNullable{Snowflake}
afk_timeout                   :: Optional{Int}
embed_enabled                 :: Optional{Bool}
embed_channel_id              :: OptionalNullable{Snowflake}
verification_level            :: Optional{Int}
default_message_notifications :: Optional{Int}
explicit_content_filter       :: Optional{Int}
roles                         :: Optional{Vector{Ekztazy.Role}}
emojis                        :: Optional{Vector{Ekztazy.Emoji}}
features                      :: Optional{Vector{String}}
mfa_level                     :: Optional{Int}
application_id                :: OptionalNullable{Snowflake}
widget_enabled                :: Optional{Bool}
widget_channel_id             :: OptionalNullable{Snowflake}
system_channel_id             :: OptionalNullable{Snowflake}
joined_at                     :: Optional{DateTime}
large                         :: Optional{Bool}
unavailable                   :: Optional{Bool}
member_count                  :: Optional{Int}
max_members                   :: Optional{Int}
voice_states                  :: Optional{Vector{Ekztazy.VoiceState}}
members                       :: Optional{Vector{Ekztazy.Member}}
channels                      :: Optional{Vector{Ekztazy.DiscordChannel}}
presences                     :: Optional{Vector{Ekztazy.Presence}}
max_presences                 :: OptionalNullable{Int}
vanity_url_code               :: OptionalNullable{String}
description                   :: OptionalNullable{String}
banner                        :: OptionalNullable{String}
```
