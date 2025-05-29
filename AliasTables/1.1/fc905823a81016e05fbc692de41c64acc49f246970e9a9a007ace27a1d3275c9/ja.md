```
probabilities(float, at::AliasTable{T}) -> Vector{<:AbstractFloat}
```

`at`のサンプリング確率を返します。返されるベクトルは、丸め誤差を考慮して1.0に合計されます。

# 例

```jldoctest
julia> AliasTables.probabilities(float, AliasTable([1, 3, 1]))
3-element Vector{Float64}:
 0.2
 0.6
 0.2
```
