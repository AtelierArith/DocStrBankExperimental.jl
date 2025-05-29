```
ProjectedTo(::Type{T}, dims...; conditioner = nothing, parameters = DefaultProjectionParameters)
```

A specification of a projection to an exponential family distribution.

The following arguments are required:

  * `Type{T}`: a type of an exponential family member to project to, e.g. `Beta`
  * `dims...`: dimensions of the distribution, e.g. `2` for `MvNormal`

The following arguments are optional:

  * `conditioner = nothing`: a conditioner to use for the projection, not all exponential family members require a conditioner, but some do, e.g. `Laplace`
  * `parameters = DefaultProjectionParameters`: parameters for the projection procedure
  * `kwargs = nothing`: Additional arguments passed to `Manopt.gradient_descent!` (optional). For details on `gradient_descent!` parameters, see the [Manopt.jl documentation](https://manoptjl.org/stable/solvers/gradient_descent/#Manopt.gradient_descent). Note, that `kwargs` passed to `project_to` take precedence over `kwargs` specified in the parameters.

```jldoctest
julia> using ExponentialFamily

julia> projected_to = ProjectedTo(Beta)
ProjectedTo(Beta)

julia> projected_to = ProjectedTo(Beta, parameters = ProjectionParameters(niterations = 10))
ProjectedTo(Beta)

julia> projected_to = ProjectedTo(MvNormalMeanCovariance, 2)
ProjectedTo(MvNormalMeanCovariance, dims = 2)

julia> projected_to = ProjectedTo(Laplace, conditioner = 2.0)
ProjectedTo(Laplace, conditioner = 2.0)
```
