get*retweets*of_me(; kwargs...) Get an array object of retweets from the owning user. This function will call the API until the desired `count` is reached or the API runs out, whichever comes first.

# Examples

```julia-repl
julia> get_retweets_of_me(count = 1000)
```
