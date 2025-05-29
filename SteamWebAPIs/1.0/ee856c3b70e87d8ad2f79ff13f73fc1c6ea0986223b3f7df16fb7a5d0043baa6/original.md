```
get_friend_list(steamid::Int)::Dict{Int,DateTime}
```

**Summary**: `get_friend_list` returns the friend Dict of any Steam user, provided their Steam Community profile visibility is set to "Public". Nothing will be returned if the profile is private. Key of Dict is steamid, value is the date on which we became friends.

# Arguments

  * `steamid`: 64 bit Steam ID to return friend list for.

# Example

```julia-repl
julia> get_friend_list(76561198202322924)
friends = Dict(76561198347283942 => Dates.DateTime("2021-12-24T06:08:57")...)
```
