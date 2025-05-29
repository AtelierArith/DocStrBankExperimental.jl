```
TwoPhotonView(ψ::T,WI1::Int,WI2::Int) where {T <: MultipleWaveguideKet}
```

状態 `ψ` は複数の波導を含みます。

2つの波導インデックスは、状態 $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$ を `i = WI1` および `j = WI2` で見ることを意味します。

インデックスが提供されていないため、基底状態が仮定されます。See [`view_waveguide`](@ref).
