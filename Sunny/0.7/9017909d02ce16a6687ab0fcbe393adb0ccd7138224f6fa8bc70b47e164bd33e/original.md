```
LocalSampler(; kT, nsweeps=1.0, propose=propose_uniform)
```

Monte Carlo simulation involving Metropolis updates to individual spins. One call to the [`step!`](@ref) function will perform `nsweeps` of MCMC sampling for a provided [`System`](@ref). The default value of `1.0` means that `step!` performs, on average, one trial update per spin.

Assuming ergodicity, the `LocalSampler` will sample from thermal equilibrium for the target temperature `kT`. 

The trial spin updates are sampled using the `propose` function. Options include [`propose_uniform`](@ref), [`propose_flip`](@ref), and [`propose_delta`](@ref). Multiple proposals can be mixed with the macro [`@mix_proposals`](@ref).

The returned object stores fields `ΔE` and `ΔS`, which represent the cumulative change to the net energy and dipole, respectively.

!!! warning "Efficiency considerations"
    Prefer [`Langevin`](@ref) sampling in most cases. Langevin dynamics will usually be much more efficient for sampling Heisenberg-like spins that vary continuously. `LocalSampler` is most useful for sampling from discrete spin states. In particular, [`propose_flip`](@ref) may be required for sampling Ising-like spins that arise due to a strong easy-axis anisotropy. For strong but finite single-ion anisotropy, consider alternating between `Langevin` and `LocalSampler` update steps.

