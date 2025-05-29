```
value(pair)
```

`pair`の`key => value`における`value`。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred value(:a => 1)
1

julia> @inferred value((:a, 1))
1
```
