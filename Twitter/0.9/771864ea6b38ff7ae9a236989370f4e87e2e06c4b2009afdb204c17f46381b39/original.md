get*user*timeline(; kwargs...) Get an array object of timeline tweets from a particular Twitter user. This function will call the API until the desired `count` is reached or the API runs out, whichever comes first.

# Examples

```julia-repl
julia> get_user_timeline(screen_name = "twitter", count = 1000)
```
