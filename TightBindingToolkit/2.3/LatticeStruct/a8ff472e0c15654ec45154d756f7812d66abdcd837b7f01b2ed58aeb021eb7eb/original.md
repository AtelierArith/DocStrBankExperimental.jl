```julia
ApplyBCToSite(site::Vector{Int64}, L::Vector{Int64}, BC::Vector{ComplexF64}) -->  Vector{Int64}
```

Returns the effective real-space offset of `site` given a lattice size `L`, and boundary conditions `BC`.
