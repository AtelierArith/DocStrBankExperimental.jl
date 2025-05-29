インタラクションのデータ。詳細は[こちら](https://discord.com/developers/docs/interactions/receiving-and-responding#interaction-object-interaction-data-structure)を参照してください。

## Fields

```
id             :: OptionalNullable{Snowflake}
name           :: OptionalNullable{String}
type           :: OptionalNullable{Int}
resolved       :: Optional{Ekztazy.ResolvedData}
options        :: Optional{Vector{Ekztazy.ApplicationCommandOption}}
custom_id      :: OptionalNullable{String}
component_type :: OptionalNullable{Int}
components     :: OptionalNullable{Vector{Ekztazy.Component}}
values         :: Optional{Vector{String}}
target_id      :: Optional{Snowflake}
```
