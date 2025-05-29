```
value(pair)
```

The `value` in a `key => value` `pair`.

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred value(:a => 1)
1

julia> @inferred value((:a, 1))
1
```
