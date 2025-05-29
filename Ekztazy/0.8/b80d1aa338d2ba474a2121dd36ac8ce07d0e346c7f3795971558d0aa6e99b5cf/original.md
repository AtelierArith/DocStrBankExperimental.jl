A [`User`](@ref)のプレゼンス。詳細は[こちら](https://discordapp.com/developers/docs/topics/gateway#presence-update)を参照してください。

## Fields

```
user       :: Ekztazy.User
roles      :: Optional{Vector{Snowflake}}
game       :: Nullable{Ekztazy.Activity}
guild_id   :: Optional{Snowflake}
status     :: String
activities :: Vector{Ekztazy.Activity}
```
