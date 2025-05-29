```
apply(ψ::Vector{<:Complex}, c::Circuit{N}) where {N}
```

returns list of expectation values from measurement operators in `c.meas` after applying circuit gates in `c.cgc` on state vector of `N` qubits `ψ`
