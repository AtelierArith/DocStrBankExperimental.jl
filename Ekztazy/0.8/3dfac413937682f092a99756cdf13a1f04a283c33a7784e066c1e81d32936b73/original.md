インタラクション。詳細は[こちら](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-structure)を参照してください。

## Fields

```
id             :: Nullable{Snowflake}
application_id :: Nullable{Snowflake}
type           :: Int
data           :: OptionalNullable{Ekztazy.InteractionData}
guild_id       :: Optional{Snowflake}
channel_id     :: Optional{Snowflake}
member         :: Optional{Ekztazy.Member}
user           :: Optional{Ekztazy.User}
token          :: String
version        :: Optional{Int}
message        :: Optional{Ekztazy.Message}
```
