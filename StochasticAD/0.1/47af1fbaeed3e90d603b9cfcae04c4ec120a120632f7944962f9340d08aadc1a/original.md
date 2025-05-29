```
InversionMethodDerivativeCoupling(; mode::Val = Val(:positive_weight), handle_zeroprob::Val = Val(true))
```

Specifies an inversion method coupling for generating perturbations from a univariate distribution. Valid choices of `mode` are `Val(:positive_weight)`, `Val(:always_right)`, and `Val(:always_left)`.

# Example

```jldoctest
julia> using StochasticAD, Distributions, Random; Random.seed!(4321);

julia> function X(p)
           return randst(Bernoulli(1 - p); derivative_coupling = InversionMethodDerivativeCoupling(; mode = Val(:always_right)))
       end
X (generic function with 1 method)

julia> stochastic_triple(X, 0.5)
StochasticTriple of Int64:
0 + 0ε + (1 with probability -2.0ε)
```
