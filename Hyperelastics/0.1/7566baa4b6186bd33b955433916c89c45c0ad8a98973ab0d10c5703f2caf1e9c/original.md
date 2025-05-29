```julia
parameter_bounds(
    _::Hyperelastics.AbstractHyperelasticModel,
    _::Hyperelastics.AbstractHyperelasticTest
) -> NamedTuple{(:lb, :ub), <:Tuple{NamedTuple{(:Gc, :μkT, :κ), <:Tuple{Float64, Float64, Any}}, Nothing}}

```

Returns a tuple of the parameter bounds provided the experimental data and model

# Arguments:

  * `ψ::AbstractHyperelasticModel`: Hyperelastic model
  * `test` or `tests`: The test or vector of tests to use in finding the parameter bounds.
