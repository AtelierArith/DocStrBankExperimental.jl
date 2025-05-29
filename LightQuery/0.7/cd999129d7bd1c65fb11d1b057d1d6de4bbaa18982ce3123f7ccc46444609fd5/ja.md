```
key(pair)
```

`pair`の`key => value`の`key`。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred key(:a => 1)
:a

julia> @inferred key((:a, 1))
:a
```
