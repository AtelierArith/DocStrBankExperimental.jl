```
key(pair)
```

The `key` in a `key => value` `pair`.

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred key(:a => 1)
:a

julia> @inferred key((:a, 1))
:a
```
