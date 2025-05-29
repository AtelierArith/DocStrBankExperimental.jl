```
timestep(ψ₀, H, t, dt, [alg], [envs]; kwargs...) -> (ψ, envs)
timestep!(ψ₀, H, t, dt, [alg], [envs]; kwargs...) -> (ψ₀, envs)
```

Time-step the state `ψ₀` with Hamiltonian `H` over a given time step `dt` at time `t`, solving the Schroedinger equation: $i ∂ψ/∂t = H ψ$.

# Arguments

  * `ψ₀::AbstractMPS`: initial state
  * `H::AbstractMPO`: operator that generates the time evolution (can be time-dependent).
  * `t::Number`: starting time of time-step
  * `dt::Number`: time-step magnitude
  * `[alg]`: algorithm to use for the time evolution. Defaults to [`TDVP`](@ref).
  * `[envs]`: MPS environment manager
