```
TwoPhotonView(ψ::T,WI::Int) where {T <: MultipleWaveguideKet}
```

状態 `ψ` は複数の波導を含み、必要な波導インデックス `WI` を持っています。

波導インデックス `i=WI` のみを指定することは、状態を観測することを意味します $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$。

インデックスが提供されていないため、基底状態が仮定されます。See [`view_waveguide`](@ref).
