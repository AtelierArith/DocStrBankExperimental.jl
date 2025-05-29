```
derivative_estimate(X, p, alg::AbstractStochasticADAlgorithm = ForwardAlgorithm(PrunedFIsBackend()); direction=nothing, alg_data::NamedTuple = (;))
```

Compute an unbiased estimate of $\frac{\mathrm{d}\mathbb{E}[X(p)]}{\mathrm{d}p}$,  the derivative of the expectation of the random function `X(p)` with respect to its input `p`.

Both `p` and `X(p)` can be any object supported by [`Functors.jl`](https://fluxml.ai/Functors.jl/stable/), e.g. scalars or abstract arrays.  The output of `derivative_estimate` has the same outer structure as `p`, but with each scalar in `p` replaced by a derivative estimate of `X(p)` with respect to that entry. For example, if `X(p) <: AbstractMatrix` and `p <: Real`, then the output would be a matrix.

The `alg` keyword argument specifies the [algorithm](public_api.md#Algorithms) used to compute the derivative estimate. For backward compatibility, an additional signature `derivative_estimate(X, p; backend, direction=nothing)` is supported, which uses `ForwardAlgorithm` by default with the supplied `backend.` The `alg_data` keyword argument can specify any additional data that specific algorithms accept or require.

When `direction` is provided, the output is only differentiated with respect to a perturbation of `p` in that direction.

# Example

```jldoctest
julia> using Distributions, Random, StochasticAD; Random.seed!(4321);

julia> derivative_estimate(rand ∘ Bernoulli, 0.5) # A random quantity that averages to the true derivative.
2.0

julia> derivative_estimate(x -> [rand(Bernoulli(x * i/4)) for i in 1:3], 0.5)
3-element Vector{Float64}:
 0.2857142857142857
 0.6666666666666666
 0.0
```
