```
show_profiles(user_data::UserInfo)
```

Get a list of all user profiles/portfolios.

# Arguments

  * `user_data::UserInfo` : API data

# Example

```julia-repl
julia> show_profiles(user_data_default)
6×6 DataFrame
 Row │ active  created_at                   id                                 is_default  name       ⋯
     │ Bool    String                       String                             Bool        String     ⋯
─────┼─────────────────────────────────────────────────────────────────────────────────────────────────
   1 │   true  2019-06-23T00:19:33.647283Z  dc06c753-2e85-4e2f-b281-3a78bc7b…        true  default    ⋯
   2 │   true  2021-05-07T21:10:07.037681Z  4617f329-2709-453b-b95d-d14727cb…       false  Julia Bot
```
