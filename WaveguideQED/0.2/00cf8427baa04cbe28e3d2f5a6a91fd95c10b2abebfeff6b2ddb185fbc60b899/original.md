```
TwoPhotonView(ψ::T,WI1::Int,WI2::Int) where {T <: MultipleWaveguideKet}
```

State `ψ` contains multiple waveguides.

Two waveguide indeces means viewing viewing the state $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$ with `i = WI1` and `j = WI2`.

No index provided so groundstate is assumed. See [`view_waveguide`](@ref).
