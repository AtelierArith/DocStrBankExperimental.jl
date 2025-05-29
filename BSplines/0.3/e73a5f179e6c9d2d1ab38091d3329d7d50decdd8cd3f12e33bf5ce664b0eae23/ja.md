```
intervalindices(basis::BSplineBasis, indices=eachindex(basis))
```

`basis` が定義されているすべての区間のインデックスを生成するイテレータを返します。つまり、`(knots(basis)[ind], knots(basis)[ind+1])` がその区間であるすべてのインデックス `ind`（昇順）を生成します。

`indices` の範囲が指定された場合、イテレータは *少なくとも1つ* の Bスプライン `basis[j] for j=indices` が非ゼロである区間のみを生成します。

# 例

```jldoctest
julia> intervalindices(BSplineBasis(3, 0:5))
3:7

julia> intervalindices(BSplineBasis(3, 0:5), 1:4)
3:6

julia> intervalindices(BSplineBasis(4, [1,2,3,4,4,4,5,6]))
BSplines.IntervalIndices{Vector{Int64}}([1, 2, 3, 4, 4, 4, 5, 6], 1:8, 3)

julia> collect(ans)
5-element Vector{Int64}:
  4
  5
  6
  9
 10
```
