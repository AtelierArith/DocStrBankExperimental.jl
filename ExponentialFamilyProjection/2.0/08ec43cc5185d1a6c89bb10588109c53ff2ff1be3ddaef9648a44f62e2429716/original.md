```
project_to(to::ProjectedTo, argument::F, supplementary..., initialpoint, kwargs...)
```

Finds the closest projection of `argument` onto the exponential family distribution specified by `to`.

# Arguments

  * `to::ProjectedTo`: Configuration for the projection. Refer to `ProjectedTo` for detailed information.
  * `argument::F`: An (un-normalized) function representing the log-PDF of an arbitrary distribution *or* a list of samples.
  * `supplementary...`: Additional distributions to project the product of `argument` and these distributions (optional).
  * `initialpoint`: Starting point for the optimization process (optional).
  * `kwargs...`: Additional arguments passed to `Manopt.gradient_descent!` (optional). For details on `gradient_descent!` parameters, see the [Manopt.jl documentation](https://manoptjl.org/stable/solvers/gradient_descent/#Manopt.gradient_descent).

# Supplementary

The `supplementary` distributions must match the type and conditioner of the target distribution specified in `to`.  Including supplementary distributions is equivalent to modified `argument` function as follows:

```julia
f_modified = (x) -> argument(x) + logpdf(supplementary[1], x) + logpdf(supplementary[2], x) + ...
```

```jldoctest
julia> using ExponentialFamily, BayesBase

julia> f = (x) -> logpdf(Beta(30.14, 2.71), x);

julia> prj = ProjectedTo(Beta; parameters = ProjectionParameters(niterations = 500))
ProjectedTo(Beta)

julia> project_to(prj, f) isa ExponentialFamily.Beta
true
```

```jldoctest
julia> using ExponentialFamily, BayesBase, StableRNGs

julia> samples = rand(StableRNG(42), Beta(30.14, 2.71), 1_000);

julia> prj = ProjectedTo(Beta; parameters = ProjectionParameters(tolerance = 1e-2))
ProjectedTo(Beta)

julia> project_to(prj, samples) isa ExponentialFamily.Beta
true
```

!!! note
    Different strategies are compatible with different types of arguments. Read optimization strategies section in the documentation for more information.

