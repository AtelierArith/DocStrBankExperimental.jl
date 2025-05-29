```
OpticalInterface{T<:Real}
```

Any subclass of OpticalInterface **must** implement the following:

```julia
processintersection(opticalinterface::OpticalInterface{T}, point::SVector{N,T}, normal::SVector{N,T}, incidentray::OpticalRay{T,N}, temperature::T, pressure::T, ::Bool, firstray::Bool = false) -> Tuple{SVector{N,T}, T, T}
insidematerial(i::OpticalInterface{T}) -> AGFFileReader.AbstractGlass
outsidematerial(i::OpticalInterface{T}) -> AGFFileReader.AbstractGlass
reflectance(i::OpticalInterface{T}) -> T
transmission(i::OpticalInterface{T}) -> T
```

See documentation for [`processintersection`](@ref) for details.
