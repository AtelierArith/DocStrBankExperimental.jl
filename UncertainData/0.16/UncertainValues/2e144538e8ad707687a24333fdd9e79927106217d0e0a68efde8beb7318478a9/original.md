```
UncertainValue(distribution::Type{D}, a::T1, b::T2;
    kwargs...) where {T1<:Number, T2 <: Number, D<:Distribution}
```

# Constructor for two-parameter distributions

`UncertainValue`s are currently implemented for the following two-parameter distributions: `Uniform`, `Normal`, `Binomial`, `Beta`, `BetaPrime`, `Gamma`, and `Frechet`.

### Arguments

  * **`a`, `b`**: Generic parameters whose meaning varies depending   on what `distribution` is provided. See the list below.
  * **`distribution`**: A valid univariate distribution from `Distributions.jl`.

Precisely what  `a` and `b` are depends on which distribution is provided.

  * `UncertainValue(Normal, μ, σ)` returns an `UncertainScalarNormallyDistributed` instance.
  * `UncertainValue(Uniform, lower, upper)` returns an `UncertainScalarUniformlyDistributed` instance.
  * `UncertainValue(Beta, α, β)` returns an `UncertainScalarBetaDistributed` instance.
  * `UncertainValue(BetaPrime, α, β)` returns an `UncertainScalarBetaPrimeDistributed` instance.
  * `UncertainValue(Gamma, α, θ)` returns an `UncertainScalarGammaDistributed` instance.
  * `UncertainValue(Frechet, α, θ)` returns an `UncertainScalarFrechetDistributed` instance.
  * `UncertainValue(Binomial, n, p)` returns an `UncertainScalarBinomialDistributed` instance.

### Keyword arguments

  * **`nσ`**: If `distribution <: Distributions.Normal`, then how many standard   deviations away from `μ` does `lower` and `upper` (i.e. both, because   they are the same distance away from `μ`) represent?
  * **`tolerance`**: A threshold determining how symmetric the uncertainties   must be in order to allow the construction of  Normal distribution   (`upper - lower > threshold` is required).
  * **`trunc_lower`**: Lower truncation bound for distributions with infinite   support. Defaults to `-Inf`.
  * **`trunc_upper`**: Upper truncation bound for distributions with infinite   support. Defaults to `Inf`.

## Examples

### Normal distribution

Normal distributions are formed by using the constructor `UncertainValue(μ, σ, Normal; kwargs...)`. This gives a normal distribution with mean μ and standard deviation σ/nσ (nσ must be given as a keyword argument).

```julia
# A normal distribution with mean = 2.3 and standard deviation 0.3.
UncertainValue(2.3, 0.3, Normal)

# A normal distribution with mean 2.3 and standard deviation 0.3/2.
UncertainValue(2.3, 0.3, Normal, nσ = 2)

# A normal distribution with mean 2.3 and standard deviation = 0.3,
truncated to the interval `[1, 3]`.
UncertainValue(2.3, 0.3, Normal, trunc_lower = 1.0, trunc_upper = 3.0)
```

### Uniform distribution

Uniform distributions are formed using the `UncertainValue(lower, upper, Uniform)` constructor.

```julia
#  A uniform distribution on `[2, 3]`
UncertainValue(-2, 3, Uniform)
```
