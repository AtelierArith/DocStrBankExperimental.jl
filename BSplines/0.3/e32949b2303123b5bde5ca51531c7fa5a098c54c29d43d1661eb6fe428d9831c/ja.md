```
intervalindices(basis::BSplineBasis, i, j, ...)
```

整数 `i`, `j`, … に対して、すべての B-スプライン `basis[i]`, `basis[j]`, … が非ゼロであるすべての区間のインデックスを生成するイテレータを返します。すなわち、`(knots(basis)[ind], knots(basis)[ind+1])` がそのような区間であるすべてのインデックス `ind`（昇順）を生成します。

# 例

```jldoctest
julia> intervalindices(BSplineBasis(3, 0:5), 3)
3:5

julia> intervalindices(BSplineBasis(3, 0:5), 4, 5)
5:6

julia> intervalindices(BSplineBasis(3, 0:5), 2, 6) # B-スプラインは重ならない
6:5

julia> intervalindices(BSplineBasis(3, 0:5), 3, 5, 4)
5:5

julia> intervalindices(BSplineBasis(4, [1,2,3,4,4,4,5,6]), 3, 5)
BSplines.IntervalIndices{Vector{Int64}}([1, 2, 3, 4, 4, 4, 5, 6], 2:4, 3)

julia> collect(ans)
2-element Vector{Int64}:
 5
 6
```
