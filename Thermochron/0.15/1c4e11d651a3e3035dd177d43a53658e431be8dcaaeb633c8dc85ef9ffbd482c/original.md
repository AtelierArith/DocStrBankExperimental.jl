```julia
MCMC(chrons::Vector{<:Chronometer}, model::NamedTuple, npoints::Int, path.agepoints::Vector, path.Tpoints::Vector, constraint::Constraint, boundary::Boundary, [detail::DetailInterval])
```

Markov chain Monte Carlo time-Temperature inversion of the thermochronometric chrons  specified as a vector `chrons` of `Chronometer` objects (`ZirconHe`, `ApatiteHe`,  `ApatiteFT`, etc.) and model parameters specified by the named tuple `model`,  with variable diffusion kinetics.

Returns a `TTResult` object containing posterior time-temperature paths,

See also `MCMC_varkinetics` for a variant with variable diffusion kinetics.

## Examples

```julia
tT = MCMC(chrons::NamedTuple, model::NamedTuple, constraint::Constraint, boundary::Boundary, [detail::DetailInterval])
```
