```
DiffLBDN(ps::AbstractLBDNParams)
```

Construct a differentiable LBDN from its direct parameterisation.

`DiffLBDN` is an alternative to [`LBDN`](@ref) that computes the explicit parameterisation [`ExplicitLBDNParams`](@ref) each time the model is called, rather than storing it in the `LBDN` object.

This model wrapper is easiest to use if you plan to update the model parameters after every call of the model. It can be trained just like any other [`Flux.jl`](http://fluxml.ai/Flux.jl/stable/) model and does not need to be re-created if the trainable parameters are updated (unlike [`LBDN`](@ref)).

However, it is slow and computationally inefficient if the model is called many times before updating the parameters (eg: in reinforcement learning). 

# Examples

The syntax to construct a `DiffLBDN` is identical to that of an [`LBDN`](@ref). 

```julia
using RobustNeuralNetworks

nu, nh, ny, γ = 1, [10, 20], 1
lbdn_params = DenseLBDNParams{Float64}(nu, nh, ny, γ)
model = DiffLBDN(lbdn_params)
```

See also [`AbstractLBDN`](@ref), [`LBDN`](@ref), [`SandwichFC`](@ref).
