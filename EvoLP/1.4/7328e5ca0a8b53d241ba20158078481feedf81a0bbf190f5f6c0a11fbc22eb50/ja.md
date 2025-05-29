```
permutation_vector_pop(n, d, pool; replacement=false, rng=Random.GLOBAL_RNG)
```

`n` 個の順列ベクトル個体を生成し、サイズは `d` で、値は `pool` からサンプリングされます。通常、`d` は `length(pool)` と等しくなります。

デフォルトでは、サンプリングは **重複なし** で行われます（`pool` が集合の場合は順列を生成します）。`replacement=true` の場合、（おそらく）重複した値の組み合わせが生成されます。

# 例

```julia
julia> permutation_vector_pop(1, 8, 1:8)
1-element Vector{Vector{Int64}}:
 [7, 3, 8, 1, 5, 6, 4, 2]

julia> permutation_vector_pop(2, 5, ["a", "b", "c", "d", "e"]; replacement=false)
2-element Vector{Vector{String}}:
 ["e", "b", "c", "d", "a"]
 ["b", "d", "a", "e", "c"]
```
