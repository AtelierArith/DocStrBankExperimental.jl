```julia
AddAnisotropicBond!( param::Param, uc::UnitCell , base::Int64 , target::Int64 , offset::Vector{Int64} , mat::Number , dist::Float64, label::String )
AddAnisotropicBond!( param::Param, uc::UnitCell , base::Int64 , target::Int64 , offset::Vector{Int64} , mat::Matrix{<:Number} , dist::Float64, label::String )
```

Add a bond with the given attributes to `param`. If given `mat` attribute is a number, it is converted into a 1x1 matrix when entered into the bond.
