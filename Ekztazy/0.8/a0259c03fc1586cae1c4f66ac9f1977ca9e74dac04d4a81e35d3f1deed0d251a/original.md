A [`Guild`](@ref) member. More details [here](https://discordapp.com/developers/docs/resources/guild#guild-member-object).

## Fields

```
user          :: Optional{Ekztazy.User}
nick          :: OptionalNullable{String}
roles         :: Vector{Snowflake}
joined_at     :: DateTime
premium_since :: OptionalNullable{DateTime}
deaf          :: Optional{Bool}
mute          :: Optional{Bool}
```
