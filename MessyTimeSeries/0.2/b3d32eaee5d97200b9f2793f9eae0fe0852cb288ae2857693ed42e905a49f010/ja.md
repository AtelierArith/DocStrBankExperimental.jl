```
rand_without_replacement(rng::StableRNGs.LehmerRNG, nT::Int64, d::Int64)
```

位置ベクトル `P` から `length(P)-d` 要素を重複なしで抽出します。

この過程で `P` は永続的に変更されます。

# 例

```jldoctest
julia> rand_without_replacement(StableRNG(1), 20, 5)
5-element Array{Int64,1}:
  1
  9
 14
 19
 20
```
