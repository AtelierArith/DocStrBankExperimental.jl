get*mentions*timeline(; kwargs...) Get an array object of mentions for a particular Twitter user. This function will call the API until the desired `count` is reached or the API runs out, whichever comes first.

# Examples

```julia-repl
julia> get_mentions_timeline(screen_name = "twitter", count = 1000)
```
