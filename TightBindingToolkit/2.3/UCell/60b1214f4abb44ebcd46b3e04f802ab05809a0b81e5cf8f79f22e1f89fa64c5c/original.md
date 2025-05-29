```julia
AddBasisSite!( uc::UnitCell , position::Vector{Float64} )
AddBasisSite!( uc::UnitCell , position::Vector{Float64} , field::Vector{Float64} )
```

Add a sublattice to the `UnitCell`  at the given real-space position, with an on-site `field`.
