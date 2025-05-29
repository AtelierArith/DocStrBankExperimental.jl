[`Guild`](@ref) インテグレーション。詳細は [こちら](https://discordapp.com/developers/docs/resources/guild#integration-object) をご覧ください。

## Fields

```
id                  :: Snowflake
name                :: String
type                :: String
enabled             :: Bool
syncing             :: Bool
role_id             :: Snowflake
expire_behaviour    :: Int
expire_grace_period :: Int
user                :: Ekztazy.User
account             :: Ekztazy.IntegrationAccount
synced_at           :: DateTime
```
