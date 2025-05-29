与えられた多項式の次数とノットベクトルからBスプライン空間を構築します。

$$
\mathcal{P}[p,k]
$$

# 例

```jldoctest
julia> p = 2
2

julia> k = KnotVector([1,3,5,6,8,9])
KnotVector([1, 3, 5, 6, 8, 9])

julia> BSplineSpace{p}(k)
BSplineSpace{2, Int64, KnotVector{Int64}}(KnotVector([1, 3, 5, 6, 8, 9]))
```
