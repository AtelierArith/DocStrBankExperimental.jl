```julia
FillHoppingHamiltonian(uc::UnitCell, k::Vector{Float64} ; OnSiteMatrices::Vector{Matrix{ComplexF64}}) --> Matrix{ComplexF64}
```

Returns the hopping Hamiltonian at momentum point `k`, corresponding to the bonds present in `UnitCell`. `OnSiteMatrices` are used for the fields, with the convention that the last matrix is the one corresponding to the chemimcal potential.
