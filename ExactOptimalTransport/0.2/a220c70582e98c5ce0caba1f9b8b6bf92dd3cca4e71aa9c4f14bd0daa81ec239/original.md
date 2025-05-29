```
wasserstein(μ, ν; metric=Euclidean(), p=Val(1), kwargs...)
```

Compute the `p`-Wasserstein distance with respect to the `metric` between measures `μ` and `ν`.

Order `p` can be provided as a scalar of type `Real` or as a parameter of a value type `Val(p)`. For certain combinations of `metric` and `p`, such as `metric=Euclidean()` and `p=Val(2)`, the computations are more efficient if `p` is specified as a value type. The remaining keyword arguments are forwarded to [`ot_cost`](@ref).

See also: [`squared2wasserstein`](@ref), [`ot_cost`](@ref)
