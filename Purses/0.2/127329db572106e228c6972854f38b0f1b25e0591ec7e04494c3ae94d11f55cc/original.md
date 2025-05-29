```
Purse(value, fs...)
```

Return `value` wrapped in a `Purse`.  Each `f` in `fs` can be either a callable or a pair a callable and a value.  If `f` is a callable, the cache will automatically be calculated by applying each `f` to `value`.  If `f` is a pair, the cache for the first element of the pair is set to the value of the second element.

# Examples

```jldoctest
julia> Purse(1.0)
Purse{Float64,Tuple{},Tuple{}}(1.0, ())

julia> Purse(2, inv)
Purse{Int64,Tuple{typeof(inv)},Tuple{Float64}}(2, (0.5,))

julia> Purse(2, inv => 0.2)
Purse{Int64,Tuple{typeof(inv)},Tuple{Float64}}(2, (0.2,))
```
