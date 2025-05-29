与えられた範囲から一様ノットベクトルを構築します。

$$
k=(k_1,\dots,k_l)
$$

# 例

```jldoctest
julia> k = UniformKnotVector(1:8)
UniformKnotVector(1:8)

julia> UniformKnotVector(8:-1:3)
UniformKnotVector(3:1:8)
```
