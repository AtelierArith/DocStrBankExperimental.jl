[`DiscordChannel`](@ref)に送信されたメッセージ。詳細は[こちら](https://discordapp.com/developers/docs/resources/channel#message-object)。

## Fields

```
id                :: Snowflake
channel_id        :: Snowflake
guild_id          :: Optional{Snowflake}
author            :: Optional{Ekztazy.User}
member            :: Optional{Ekztazy.Member}
content           :: Optional{String}
timestamp         :: Optional{DateTime}
edited_timestamp  :: OptionalNullable{DateTime}
tts               :: Optional{Bool}
mention_everyone  :: Optional{Bool}
mentions          :: Optional{Vector{Ekztazy.User}}
mention_roles     :: Optional{Vector{Snowflake}}
attachments       :: Optional{Vector{Ekztazy.Attachment}}
message_reference :: Optional{Ekztazy.MessageReference}
embeds            :: Optional{Vector{Ekztazy.Embed}}
reactions         :: Optional{Vector{Ekztazy.Reaction}}
nonce             :: OptionalNullable{Snowflake}
pinned            :: Optional{Bool}
webhook_id        :: Optional{Snowflake}
type              :: Optional{Int}
activity          :: Optional{Ekztazy.MessageActivity}
application       :: Optional{Ekztazy.MessageApplication}
```
