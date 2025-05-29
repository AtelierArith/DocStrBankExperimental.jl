```
UncertainValue(distribution::Type{D}, a::T1, b::T2, c::T3;
    kwargs...) where {T1<:Number, T2<:Number, T3<:Number, D<:Distribution}
```

## Constructor for three-parameter distributions

Currently implemented distributions are `BetaBinomial`.

### Arguments

  * **`a`, `b`, `c`**: Generic parameters whose meaning varies depending   on what `distribution` is provided. See the list below.
  * **`distribution`**: A valid univariate distribution from `Distributions.jl`.

Precisely what `a`, `b` and `c` are depends on which distribution is provided.

  * `UncertainValue(BetaBinomial, n, α, β)` returns an `UncertainScalarBetaBinomialDistributed` instance.

### Keyword arguments

  * **`nσ`**: If `distribution <: Distributions.Normal`, then how many standard   deviations away from `μ` does `lower` and `upper` (i.e. both, because   they are the same distance away from `μ`) represent?
  * **`tolerance`**: A threshold determining how symmetric the uncertainties   must be in order to allow the construction of  Normal distribution   (`upper - lower > threshold` is required).
  * **`trunc_lower`**: Lower truncation bound for distributions with infinite   support. Defaults to `-Inf`.
  * **`trunc_upper`**: Upper truncation bound for distributions with infinite   support. Defaults to `Inf`.

## Examples

### BetaBinomial distribution

Normal distributions are formed by using the constructor `UncertainValue(μ, σ, Normal; kwargs...)`. This gives a normal distribution with mean μ and standard deviation σ/nσ (nσ must be given as a keyword argument).

```julia
# A beta binomial distribution with n = 100 trials and parameters α = 2.3 and
# β = 5
UncertainValue(100, 2.3, 5, BetaBinomial)
```
