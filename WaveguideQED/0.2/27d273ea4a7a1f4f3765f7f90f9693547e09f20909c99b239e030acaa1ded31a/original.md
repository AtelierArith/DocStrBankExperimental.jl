```
OnePhotonView(ψ::T,WI::Int,index::I) where {T<:MultipleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

ψ contains only a multiple waveguides and waveguide index `WI` is needed. `index` should follow syntax outlined in [`view_waveguide`](@ref).
