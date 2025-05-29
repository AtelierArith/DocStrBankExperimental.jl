```
Acoustic{T<:AbstractFloat,Dim}(ρ::T, c::Complex{T})
Acoustic(ρ::T, c::Union{T,Complex{AbstractFloat}}, Dim::Integer)
```

Physical properties for a homogenous isotropic acoustic medium with wavespeed (c) and density (ρ)

Simulations in this medium produce scalar (1D) fields in Dim dimensions.
