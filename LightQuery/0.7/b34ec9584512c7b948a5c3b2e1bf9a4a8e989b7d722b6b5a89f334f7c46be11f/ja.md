```
By(sorted, key_function)
```

`sorted`が`key_function`によって事前にソートされていることに注意してください。[`Group`](@ref)やさまざまな結合と一緒に使用します。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> @inferred By([1, -2], abs)
By{Array{Int64,1},typeof(abs)}([1, -2], abs)
```
