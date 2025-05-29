```
sparse_init([rng], rows, cols; sparsity, std = 0.01) -> Array
sparse_init([rng]; kw...) -> Function
```

`rows, cols` のサイズの `Matrix{Float32}` を返します。各列には `sparsity` で与えられる固定の割合のゼロ要素が含まれます。非ゼロ要素は平均がゼロ、標準偏差が `std` の正規分布に従います。

このメソッドは [1] で説明されています。

# 例

```jldoctest; setup = :(using Random; Random.seed!(0))
julia> count(iszero, Flux.sparse_init(10, 10, sparsity=1/5))
20

julia> sum(0 .== Flux.sparse_init(10, 11, sparsity=0.9), dims=1)
1×11 Matrix{Int64}:
 9  9  9  9  9  9  9  9  9  9  9

julia> Dense(3 => 10, tanh; init=Flux.sparse_init(sparsity=0.5))
Dense(3 => 10, tanh)  # 40 parameters

julia> count(iszero, ans.weight, dims=1)
1×3 Matrix{Int64}:
 5  5  5
```

# 参考文献

[1] Martens, J, "Deep learning via Hessian-free optimization" *Proceedings of the 27th International Conference on International Conference on Machine Learning*. 2010.
