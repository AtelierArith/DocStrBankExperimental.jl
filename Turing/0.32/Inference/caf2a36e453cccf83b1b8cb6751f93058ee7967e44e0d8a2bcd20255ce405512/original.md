```
HMC(ϵ::Float64, n_leapfrog::Int; adtype::ADTypes.AbstractADType = AutoForwardDiff())
```

Hamiltonian Monte Carlo sampler with static trajectory.

# Arguments

  * `ϵ`: The leapfrog step size to use.
  * `n_leapfrog`: The number of leapfrog steps to use.
  * `adtype`: The automatic differentiation (AD) backend.   If not specified, `ForwardDiff` is used, with its `chunksize` automatically determined.

# Usage

```julia
HMC(0.05, 10)
```

# Tips

If you are receiving gradient errors when using `HMC`, try reducing the leapfrog step size `ϵ`, e.g.

```julia
# Original step size
sample(gdemo([1.5, 2]), HMC(0.1, 10), 1000)

# Reduced step size
sample(gdemo([1.5, 2]), HMC(0.01, 10), 1000)
```
