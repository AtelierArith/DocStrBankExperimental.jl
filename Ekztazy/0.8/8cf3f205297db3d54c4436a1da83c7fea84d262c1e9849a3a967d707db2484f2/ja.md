[`User`](@ref) アクティビティ。詳細は[こちら](https://discordapp.com/developers/docs/topics/gateway#activity-object)を参照してください。

## フィールド

```
name           :: String
type           :: Int
url            :: OptionalNullable{String}
timestamps     :: Optional{Ekztazy.ActivityTimestamps}
application_id :: Optional{Snowflake}
details        :: OptionalNullable{String}
state          :: OptionalNullable{String}
emoji          :: OptionalNullable{Ekztazy.ActivityEmoji}
party          :: Optional{Ekztazy.ActivityParty}
assets         :: Optional{Ekztazy.ActivityAssets}
secrets        :: Optional{Ekztazy.ActivitySecrets}
instance       :: Optional{Bool}
flags          :: Optional{Int}
```
