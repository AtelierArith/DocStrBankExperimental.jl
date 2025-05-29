サブノットベクトルを表す型。

$$
k=(k_1,\dots,k_l)
$$

# 例

```jldoctest
julia> k = knotvector"1 11 211"
KnotVector([1, 3, 4, 6, 6, 7, 8])

julia> view(k, 2:5)
SubKnotVector([3, 4, 6, 6])
```
