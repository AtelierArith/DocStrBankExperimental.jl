```
NUTS(n_adapts::Int, δ::Float64; max_depth::Int=10, Δ_max::Float64=1000.0, init_ϵ::Float64=0.0; adtype::ADTypes.AbstractADType=AutoForwardDiff()
```

No-U-Turn Sampler (NUTS) sampler.

Usage:

```julia
NUTS()            # Use default NUTS configuration.
NUTS(1000, 0.65)  # Use 1000 adaption steps, and target accept ratio 0.65.
```

Arguments:

  * `n_adapts::Int` : The number of samples to use with adaptation.
  * `δ::Float64` : Target acceptance rate for dual averaging.
  * `max_depth::Int` : Maximum doubling tree depth.
  * `Δ_max::Float64` : Maximum divergence during doubling tree.
  * `init_ϵ::Float64` : Initial step size; 0 means automatically searching using a heuristic procedure.
  * `adtype::ADTypes.AbstractADType` : The automatic differentiation (AD) backend.   If not specified, `ForwardDiff` is used, with its `chunksize` automatically determined.
