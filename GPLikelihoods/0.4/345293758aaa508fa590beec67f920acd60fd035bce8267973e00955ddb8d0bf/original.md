```
NegativeBinomialLikelihood(param::NBParam, invlink::Union{Function,Link})
```

There are many possible parametrizations for the Negative Binomial likelihood. We follow the convention laid out in p.137 of [^Hilbe'11] and provide some common parametrizations. The `NegativeBinomialLikelihood` has a special structure; the first type parameter `NBParam` defines in what parametrization the latent function is used, and contains the other (scalar) parameters. `NBParam` itself has two subtypes:

  * `NBParamProb` for parametrizations where `f -> p`, the probability of success of a Bernoulli event
  * `NBParamMean` for parametrizations where `f -> μ`, the expected number of events

## `NBParam` predefined types

### `NBParamProb` types with `p = invlink(f)` the probability of success or failure

  * [`NBParamSuccess`](@ref): Here `p = invlink(f)` is the probability of success. This is the definition used in [`Distributions.jl`](https://juliastats.org/Distributions.jl/latest/univariate/#Distributions.NegativeBinomial).
  * [`NBParamFailure`](@ref): Here `p = invlink(f)` is the probability of a failure

### `NBParamMean` types with `μ = invlink(f)` the mean/expected number of events

  * [`NBParamI`](@ref): Mean is linked to `f` and variance is given by `μ(1 + α)`
  * [`NBParamII`](@ref): Mean is linked to `f` and variance is given by `μ(1 + α * μ)`
  * [`NBParamPower`](@ref): Mean is linked to `f` and variance is given by `μ(1 + α * μ^ρ)`

To create a new parametrization, you need to:

  * create a new type `struct MyNBParam{T} <: NBParam; myparams::T; end`;
  * dispatch `(l::NegativeBinomialLikelihood{<:MyNBParam})(f::Real)`, which must return a [`NegativeBinomial`](https://juliastats.org/Distributions.jl/latest/univariate/#Distributions.NegativeBinomial) from `Distributions.jl`.

`NegativeBinomial` follows the parametrization of [`NBParamSuccess`](@ref), i.e. the first argument is the number of successes and the second argument is the probability of success.

## Examples

```julia-repl
julia> NegativeBinomialLikelihood(NBParamSuccess(10), logistic)(2.0)
NegativeBinomial{Float64}(r=10.0, p=0.8807970779778824)
julia> NegativeBinomialLikelihood(NBParamFailure(10), logistic)(2.0)
NegativeBinomial{Float64}(r=10.0, p=0.11920292202211757)

julia> d = NegativeBinomialLikelihood(NBParamI(3.0), exp)(2.0)
NegativeBinomial{Float64}(r=2.4630186996435506, p=0.25)
julia> mean(d) ≈ exp(2.0)
true
julia> var(d) ≈ exp(2.0) * (1 + 3.0)
true
```

[^Hilbe'11]: Hilbe, Joseph M. Negative binomial regression. Cambridge University Press, 2011.
