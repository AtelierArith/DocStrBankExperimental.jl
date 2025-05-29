```julia
mcmc_with_warmup(
    rng,
    ℓ,
    N;
    initialization,
    warmup_stages,
    algorithm,
    reporter
)

```

Perform MCMC with NUTS, including warmup which is not returned. Return a `NamedTuple` of

  * `posterior_matrix`, a matrix of position vectors, indexes by `[parameter_index, draw_index]`
  * `tree_statistics`, a vector of tree statistics for each sample
  * `κ` and `ϵ`, the adapted metric and stepsize.

# Arguments

  * `rng`: the random number generator, eg `Random.default_rng()`.
  * `ℓ`: the log density, supporting the API of the `LogDensityProblems` package
  * `N`: the number of samples for inference, after the warmup.

# Keyword arguments

  * `initialization`: see below.
  * `warmup_stages`: a sequence of warmup stages. See [`default_warmup_stages`](@ref) and [`fixed_stepsize_warmup_stages`](@ref); the latter requires an `ϵ` in initialization.
  * `algorithm`: see [`NUTS`](@ref). It is very unlikely you need to modify this, except perhaps for the maximum depth.
  * `reporter`: how progress is reported. By default, verbosely for interactive sessions using the log message mechanism (see [`LogProgressReport`](@ref), and no reporting for non-interactive sessions (see [`NoProgressReport`](@ref)).

# Initialization

The `initialization` keyword argument should be a `NamedTuple` which can contain the following fields (all of them optional and provided with reasonable defaults):

  * `q`: initial position. *Default*: random (uniform [-2,2] for each coordinate).
  * `κ`: kinetic energy specification. *Default*: Gaussian with identity matrix.
  * `ϵ`: a scalar for initial stepsize, or `nothing` for heuristic finders.

# Usage examples

Using a fixed stepsize:

```julia
mcmc_with_warmup(rng, ℓ, N;
                 initialization = (ϵ = 0.1, ),
                 warmup_stages = fixed_stepsize_warmup_stages())
```

Starting from a given position `q₀` and kinetic energy scaled down (will still be adapted):

```julia
mcmc_with_warmup(rng, ℓ, N;
                 initialization = (q = q₀, κ = GaussianKineticEnergy(5, 0.1)))
```

Using a dense metric:

```julia
mcmc_with_warmup(rng, ℓ, N;
                 warmup_stages = default_warmup_stages(; M = Symmetric))
```

Disabling the initial stepsize search (provided explicitly, still adapted):

```julia
mcmc_with_warmup(rng, ℓ, N;
                 initialization = (ϵ = 1.0, ),
                 warmup_stages = default_warmup_stages(; stepsize_search = nothing))
```
