```
TwoPhotonView(ψ::T,WI::I) where {T <: MultipleWaveguideKet,I<:Union{Vector{Int64},Tuple{Vararg{Int64}}}}
```

State `ψ` contains multiple waveguides.

Waveguide indeces provided as tuple or vector of length 2, means viewing viewing the state $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$ with `i = WI[1]` and `j = WI[2]`.

No index provided so groundstate is assumed. See [`view_waveguide`](@ref).
