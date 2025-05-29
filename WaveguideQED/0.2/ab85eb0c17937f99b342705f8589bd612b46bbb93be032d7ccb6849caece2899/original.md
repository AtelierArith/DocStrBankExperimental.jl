```
TwoPhotonView(ψ::T,WI::Int) where {T <: MultipleWaveguideKet}
```

State `ψ` contains multiple waveguides and waveguide index `WI` required. 

Only one waveguide index `i=WI` means viewing the state $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$.

No index provided so groundstate is assumed. See [`view_waveguide`](@ref).
