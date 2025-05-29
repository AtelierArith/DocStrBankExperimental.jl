```
find_fixpoint(nw::Network, [x0::NWState=NWState(nw)], [p::NWParameter=x0.p]; kwargs...)
find_fixpoint(nw::Network, x0::AbstractVector, p::AbstractVector; kwargs...)
find_fixpoint(nw::Network, x0::AbstractVector; kwargs...)
```

Convenience wrapper around `SteadyStateProblem` from SciML-ecosystem. Constructs and solves the steady state problem, returns found value wrapped as `NWState`.
