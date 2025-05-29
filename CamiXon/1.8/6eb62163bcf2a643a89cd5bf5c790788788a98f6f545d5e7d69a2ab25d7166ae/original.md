```
updatePos!(pos::Pos, E::T, Veff::Vector{T}, grid::CamiDiff.Grid{T}) where T<:Real
```

Update the [`Pos`](@ref) object starting from the energy `E`, and the effective  potential energy (screened Coulomb potential) `Veff[n]` tabulated on the [`CamiDiff.Grid`](@extref). 
