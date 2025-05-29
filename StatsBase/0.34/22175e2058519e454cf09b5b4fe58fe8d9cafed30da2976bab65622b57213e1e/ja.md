```
uweights(s::Integer)
uweights(::Type{T}, s::Integer) where T<:Real
```

長さ `s` の `UnitWeights` ベクトルを、型 `T` の重み要素で構成します。すべての重み要素は同じく1です。

# 例

```julia-repl
julia> uweights(3)
3-element UnitWeights{Int64}:
 1
 1
 1

julia> uweights(Float64, 3)
3-element UnitWeights{Float64}:
 1.0
 1.0
 1.0
```
