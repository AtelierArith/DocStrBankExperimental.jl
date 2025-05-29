```
AlignedBags(k::Vector{<:Integer})
```

`Vector` `k` から各インスタンスが属するバッグのインデックスを指定して新しい [`AlignedBags`](@ref) 構造体を構築します。これが不可能な場合は `ArgumentError` をスローします。

# 例

```jldoctest
julia> AlignedBags([1, 1, 2, 2, 2, 4])
AlignedBags{Int64}(UnitRange{Int64}[1:2, 3:5, 0:-1, 6:6])
```
