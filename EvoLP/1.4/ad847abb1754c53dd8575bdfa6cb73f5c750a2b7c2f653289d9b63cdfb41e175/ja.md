```
unif_rand_vector_pop(n, lb, ub; rng=Random.GLOBAL_RNG)
```

下限 `lb` と上限 `ub` の間で一様ランダム分布を使用して、`n` 個のベクトル個体の集団を生成します。

`lb` と `ub` は同じ次元の配列でなければなりません。

# 例

```julia
julia> unif_rand_vector_pop(3, [-1, -1], [1, 1])
3-element Vector{Vector{Float64}}:
 [-0.16338687344459046, 0.31576097298524064]
 [-0.941510876597899, 0.8219576462978224]
 [-0.377090051761797, -0.28434454028992096]
```
