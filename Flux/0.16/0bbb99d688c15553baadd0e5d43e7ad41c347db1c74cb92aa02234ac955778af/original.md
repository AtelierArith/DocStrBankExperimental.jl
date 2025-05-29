```
sparse_init([rng], rows, cols; sparsity, std = 0.01) -> Array
sparse_init([rng]; kw...) -> Function
```

Return a `Matrix{Float32}` of size `rows, cols` where each column contains a fixed fraction of zero elements given by `sparsity`. Non-zero elements are normally distributed with a mean of zero and standard deviation `std`.

This method is described in [1].

# Examples

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

# References

[1] Martens, J, "Deep learning via Hessian-free optimization" *Proceedings of the 27th International Conference on International Conference on Machine Learning*. 2010.
