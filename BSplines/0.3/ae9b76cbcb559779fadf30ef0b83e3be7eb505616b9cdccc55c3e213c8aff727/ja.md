```
intervalindex(vec, x[, start])
```

`v` が `AbstractVector` の場合、`vec[i] ≤ x ≤ vec[end]` かつ `vec[i] < vec[end]` を満たす最大のインデックス `i` を返します。該当するインデックスが存在しない場合は `nothing` を返します。ベクトル `vec` は昇順にソートされていると仮定します。

`vec` が [`BSplineBasis`](@ref) の場合、`intervalindex(knots(vec), x[, start])` を返します。

`start` が指定されている場合、インデックス `start` から前方または後方に線形探索が行われます。`start` が指定されていない場合は、二分探索が行われます。

# 例

```jldoctest
julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 2.5)
3

julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 7) # nothing を返す

julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 1)
2

julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 4)
7

julia> intervalindex([1,1,2,3,4,4,4,5,6,6], 6.0)
8
```
