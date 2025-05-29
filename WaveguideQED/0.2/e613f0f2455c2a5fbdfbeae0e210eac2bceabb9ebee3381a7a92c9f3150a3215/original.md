```
OnePhotonView(ψ::T,index::I) where {T<:SingleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

ψ contains only a single waveguide and no waveguide index is needed. `index` should follow syntax outlined in [`view_waveguide`](@ref).
