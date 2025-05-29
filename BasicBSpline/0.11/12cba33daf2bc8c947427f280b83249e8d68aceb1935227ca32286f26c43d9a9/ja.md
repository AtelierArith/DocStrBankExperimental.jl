Bスプライン空間の次元を返します。

$$
\dim(\mathcal{P}[p,k])
=\# k - p -1
$$

# 例

```jldoctest
julia> dim(BSplineSpace{1}(KnotVector([1,2,3,4,5,6,7])))
5

julia> dim(BSplineSpace{1}(KnotVector([1,2,4,4,4,6,7])))
5

julia> dim(BSplineSpace{1}(KnotVector([1,2,3,5,5,5,7])))
5
```
