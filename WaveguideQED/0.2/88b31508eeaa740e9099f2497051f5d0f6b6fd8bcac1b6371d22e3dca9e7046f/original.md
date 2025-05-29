```
TwoPhotonView(ψ::T,WI::F,index::I)  where {T<:MultipleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}},F<:Union{Vector{Int64},Tuple{Vararg{Int64}}}}
```

State `ψ` contains multiple waveguides.

Waveguide indeces provided as tuple or vector of length 2, means viewing viewing the state $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$ with `i = WI[1]` and `j = WI[2]`.

Index should follow syntax highlighted in [`view_waveguide`](@ref).
