get*home*timeline(; kwargs...) Get an array object of timeline tweets from the owning user. This function will call the API until the desired `count` is reached or the API runs out, whichever comes first.

# Examples

```julia-repl
julia> get_home_timeline(count = 1000)
```
