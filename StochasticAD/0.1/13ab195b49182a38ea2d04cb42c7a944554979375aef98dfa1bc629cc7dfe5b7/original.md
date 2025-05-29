```
stochastic_triple(X, p; backend=PrunedFIsBackend(), direction=nothing)
stochastic_triple(p; backend=PrunedFIsBackend(), direction=nothing)
```

For any `p` that is supported by [`Functors.jl`](https://fluxml.ai/Functors.jl/stable/), e.g. scalars or abstract arrays, differentiate the output with respect to each value of `p`, returning an output of similar structure to `p`, where a particular value contains the stochastic-triple output of `X` when perturbing the corresponding value in `p` (i.e. replacing the original value `x` with `x + ε`).

When `direction` is provided, return only the stochastic-triple output of `X` with respect to a perturbation of `p` in that particular direction. When `X` is not provided, the identity function is used. 

The `backend` keyword argument describes the algorithm used by the third component of the stochastic triple, see [technical details](devdocs.md) for more details.

# Example

```jldoctest
julia> using Distributions, Random, StochasticAD; Random.seed!(4321);

julia> stochastic_triple(rand ∘ Bernoulli, 0.5)
StochasticTriple of Int64:
0 + 0ε + (1 with probability 2.0ε)
```
