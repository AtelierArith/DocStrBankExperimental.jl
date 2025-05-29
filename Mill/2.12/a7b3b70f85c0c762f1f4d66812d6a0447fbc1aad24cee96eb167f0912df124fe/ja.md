```
ScatteredBags(k::Vector{<:Integer})
```

`Vector` `k` から各インスタンスが属するバッグのインデックスを指定して新しい [`ScatteredBags`](@ref) 構造体を構築します。

# 例

```jldoctest
julia> ScatteredBags([2, 2, 1, 1, 1, 3])
ScatteredBags{Int64}([[3, 4, 5], [1, 2], [6]])
```
