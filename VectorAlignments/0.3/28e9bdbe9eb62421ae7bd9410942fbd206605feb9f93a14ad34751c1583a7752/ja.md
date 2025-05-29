ベクトルのシーケンスに対する最短共通スーパーシーケンスを見つけます。

# 例

```jldoctest
julia> scs([1,3,5], [1,2,3])
4-element Vector{Any}:
 1
 2
 3
 5
```

```julia
scs(v; norm, cf)

```
