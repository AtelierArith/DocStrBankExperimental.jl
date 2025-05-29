```julia
AddIsotropicBonds!( uc::UnitCell{T} , dist::Float64 , mats::Number , label::String; checkOffsetRange::Int64=1 , subs::Vector{Int64}=collect(1:length(uc.basis)))
AddIsotropicBonds!( uc::UnitCell{T} , dist::Float64 , mats::Array{<:Number, T} , label::String; checkOffsetRange::Int64=1 , subs::Vector{Int64}=collect(1:length(uc.basis)) )
```

Add a set of "isotropic" bonds, which are the same for each pair of sites at the given distance.  If given `mat` attribute is a number, it is converted into a 1x1 matrix when entered into the bond. The input `checkOffsetRange` must be adjusted depending on the input distance.  The optional input `subs` is meant for isotropic bonds when only a subset of sublattices are involved.
