```julia
FindLinks(Ham::Hamiltonian, subset::Vector{Int64}) --> Tuple{Matrix{ComplexF64}, Matrix{ComplexF64}}
```

Function to get the linking matrices on each neighbouring point in the `BZ`. On a bond connecting k*i and k*j, the linking matrix U is defined such that U[m, n] = <v^m[k*i]|v^n[k*j]> where states[k*j[1], k*j[2]][:, m] = v^m[k*j], the mth eigenstate at momentum k*j.
