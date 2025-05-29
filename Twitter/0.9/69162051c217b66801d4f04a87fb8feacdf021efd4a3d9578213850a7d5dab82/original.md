get*friends*ids(; kwargs...) Get a Dict object of follower ids from a particular Twitter user. This function will call the API as until the desired `count` is reached or the API runs out, whichever comes first.

# Examples

```julia-repl
julia> get_friends_ids(screen_name = "barackobama", count = 1000)
```
