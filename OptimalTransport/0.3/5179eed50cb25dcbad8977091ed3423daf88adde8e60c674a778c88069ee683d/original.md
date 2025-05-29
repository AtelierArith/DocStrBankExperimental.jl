```
sinkhorn2(
    μ, ν, C, ε, alg=SinkhornGibbs(); regularization=false, plan=nothing, kwargs...
)
```

Solve the entropically regularized optimal transport problem with source and target marginals `μ` and `ν`, cost matrix `C` of size `(length(μ), length(ν))`, and entropic regularization parameter `ε`, and return the optimal cost.

A pre-computed optimal transport `plan` may be provided. The other keyword arguments supported here are the same as those in the [`sinkhorn`](@ref) function.

!!! note
    As the `sinkhorn2` function in the Python Optimal Transport package, this function returns the optimal transport cost without the regularization term. The cost with the regularization term can be computed by setting `regularization=true`.


See also: [`sinkhorn`](@ref)
