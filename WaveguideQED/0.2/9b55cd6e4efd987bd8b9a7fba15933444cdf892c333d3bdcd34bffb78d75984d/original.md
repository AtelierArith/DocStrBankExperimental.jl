```
TwoPhotonView(ψ::T,index::I) where {T <: SingleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

State `ψ` only contains one waveguide. Index should follow syntax highlighted in [`view_waveguide`](@ref).
