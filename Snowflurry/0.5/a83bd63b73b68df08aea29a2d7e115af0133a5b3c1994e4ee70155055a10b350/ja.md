```
get_excluded_positions(
    c::Union{LineConnectivity,LatticeConnectivity}
)::Vector{Tuple{Int, Int}}
```

接続のための `excluded_positions` のリストを返します。

# 例

```jldoctest
julia> get_excluded_positions(LatticeConnectivity(3, 4, [1, 3]))
2-element Vector{Int64}:
 1
 3

```
