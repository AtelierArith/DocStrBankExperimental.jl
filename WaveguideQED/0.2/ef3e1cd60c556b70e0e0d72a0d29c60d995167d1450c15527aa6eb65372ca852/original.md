```
TwoPhotonView(ψ::T,WI1::Int,WI2::Int,index::I)  where {T<:MultipleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

State `ψ` contains multiple waveguides.

Two waveguide indeces means viewing viewing the state $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$ with `i = WI1` and `j = WI2`.

Index should follow syntax highlighted in [`view_waveguide`](@ref).
