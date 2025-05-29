```
bose_hubbard_interaction(address)
```

Return $Σ_i n_i (n_i-1)$ for computing the Bose-Hubbard on-site interaction (without the $U$ prefactor.)

# Example

```jldoctest
julia> Hamiltonians.bose_hubbard_interaction(BoseFS{4,4}((2,1,1,0)))
2
julia> Hamiltonians.bose_hubbard_interaction(BoseFS{4,4}((3,0,1,0)))
6
```
