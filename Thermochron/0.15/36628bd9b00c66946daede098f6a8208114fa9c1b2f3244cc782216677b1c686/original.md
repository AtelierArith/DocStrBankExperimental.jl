```julia
MCMC_varkinetics(chrons::Vector{<:Chronometer}, model::NamedTuple, npoints::Int, path.agepoints::Vector, path.Tpoints::Vector, constraint::Constraint, boundary::Boundary, [detail::DetailInterval])
```

Markov chain Monte Carlo time-Temperature inversion of the thermochronometric chrons  specified as a vector `chrons` of `Chronometer` objects (`ZirconHe`, `ApatiteHe`,  `ApatiteFT`, etc.) and model parameters specified by the named tuple `model`,  with variable diffusion kinetics.

Returns a `TTResult` object containing posterior time-temperature paths, and a `KineticResult` object containing the posterior kinetic parameters.

See also `MCMC` for a variant with constant diffusion kinetics.

## Examples

```julia
tT, kinetics = MCMC_varkinetics(chrons::NamedTuple, model::NamedTuple, constraint::Constraint, boundary::Boundary, [detail::DetailInterval])
```
