```
OpticalInterface{T<:Real}
```

OpticalInterfaceの任意のサブクラスは、以下を**必ず**実装しなければなりません：

```julia
processintersection(opticalinterface::OpticalInterface{T}, point::SVector{N,T}, normal::SVector{N,T}, incidentray::OpticalRay{T,N}, temperature::T, pressure::T, ::Bool, firstray::Bool = false) -> Tuple{SVector{N,T}, T, T}
insidematerial(i::OpticalInterface{T}) -> AGFFileReader.AbstractGlass
outsidematerial(i::OpticalInterface{T}) -> AGFFileReader.AbstractGlass
reflectance(i::OpticalInterface{T}) -> T
transmission(i::OpticalInterface{T}) -> T
```

詳細については[`processintersection`](@ref)のドキュメントを参照してください。
