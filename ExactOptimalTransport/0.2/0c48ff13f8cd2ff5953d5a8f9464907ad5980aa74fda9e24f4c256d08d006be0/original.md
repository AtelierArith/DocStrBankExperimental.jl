```
squared2wasserstein(μ, ν; metric=Euclidean(), kwargs...)
```

Compute the squared 2-Wasserstein distance with respect to the `metric` between measures `μ` and `ν`.

The remaining keyword arguments are forwarded to [`ot_cost`](@ref).

See also: [`wasserstein`](@ref), [`ot_cost`](@ref)
