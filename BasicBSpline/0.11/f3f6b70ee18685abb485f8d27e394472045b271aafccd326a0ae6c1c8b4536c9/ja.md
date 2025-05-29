与えられたBスプライン空間が退化しているかどうかを確認します。

# 例

```jldoctest
julia> isdegenerate(BSplineSpace{2}(KnotVector([1,3,5,6,8,9])))
false

julia> isdegenerate(BSplineSpace{1}(KnotVector([1,3,3,3,8,9])))
true
```
