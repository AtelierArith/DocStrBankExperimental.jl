```
TwoPhotonView(ψ::T,WI::Int,index::I)  where {T<:MultipleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

State `ψ` contains multiple waveguides.

Only one waveguide index `i=WI` means viewing the state $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$.

Index should follow syntax highlighted in [`view_waveguide`](@ref).
