```
Yij(i::AbstractString, j::AbstractString, net::CommonOPF.Network)::Union{ComplexF64, Matrix{ComplexF64}}
```

Returns either:

  * entry of admittance matrix at i,j for single phase networks or
  * 3x3 admittance sub-matrix for the phases connecting busses i and j
