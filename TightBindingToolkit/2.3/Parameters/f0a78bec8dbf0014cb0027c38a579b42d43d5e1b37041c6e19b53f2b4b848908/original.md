```julia
AddSimilarBond!(param::Param{T, R}, uc::UnitCell{T2}, bond::Bond{T} ;  subs::Vector{Int64}=collect(1:length(uc.basis)), checkOffsetRange::Int64=2) where {T, R}
AddSimilarBond!(param::Param{T, R}, uc::UnitCell{T2}, base::Int64, target::Int64, offset::Vector{Int64}, mat::Array{ComplexF64, T}, dist::Float64, label::String ;  subs::Vector{Int64}=collect(1:length(uc.basis)), checkOffsetRange::Int64=2) where {T, R}
```

Function to add bonds which are not completely isotropic, but are still related by translation (not by the unit cell primitives but by the underlying lattice primitives).
