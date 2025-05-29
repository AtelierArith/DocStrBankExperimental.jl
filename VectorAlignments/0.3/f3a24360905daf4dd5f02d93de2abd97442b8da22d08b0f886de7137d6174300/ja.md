ベクトルのシーケンスに対する最長共通部分列を見つけます。

# 例

```jldoctest
julia> lcs([1,3,5], [1,2,3])
2-element Vector{Any}:
 1
 3
```

```julia
lcs(v; norm, cf)

```
