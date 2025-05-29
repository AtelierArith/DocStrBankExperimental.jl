Bスプライン空間の正確な次元。

# 例

```jldoctest
julia> exactdim_I(BSplineSpace{1}(KnotVector([1,2,3,4,5,6,7])))
5

julia> exactdim_I(BSplineSpace{1}(KnotVector([1,2,4,4,4,6,7])))
4

julia> exactdim_I(BSplineSpace{1}(KnotVector([1,2,3,5,5,5,7])))
3
```
