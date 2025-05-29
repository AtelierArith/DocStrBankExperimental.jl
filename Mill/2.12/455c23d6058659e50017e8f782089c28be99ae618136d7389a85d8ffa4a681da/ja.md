```
AlignedBags(bags::UnitRange{<:Integer}...)
```

引数のバッグから新しい [`AlignedBags`](@ref) 構造体を構築します。

# 例

```jldoctest
julia> AlignedBags(1:3, 4:8)
AlignedBags{Int64}(UnitRange{Int64}[1:3, 4:8])
```
