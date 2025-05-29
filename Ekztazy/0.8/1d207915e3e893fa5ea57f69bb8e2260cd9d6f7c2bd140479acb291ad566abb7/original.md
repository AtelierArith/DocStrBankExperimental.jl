アプリケーションコマンド。詳細は[こちら](https://discord.com/developers/docs/interactions/application-commands#application-commands)を参照してください。

## Fields

```
id                  :: OptionalNullable{Snowflake}
type                :: Optional{Int}
application_id      :: Snowflake
guild_id            :: Optional{Snowflake}
name                :: String
description         :: String
options             :: Optional{Vector{Ekztazy.ApplicationCommandOption}}
default_permissions :: Optional{Bool}
version             :: Optional{Snowflake}
```
