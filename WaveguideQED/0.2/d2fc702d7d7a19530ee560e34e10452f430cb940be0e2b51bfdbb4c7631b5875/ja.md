```
TwoPhotonView(ψ::T,WI::I) where {T <: MultipleWaveguideKet,I<:Union{Vector{Int64},Tuple{Vararg{Int64}}}}
```

状態 `ψ` は複数の波導を含みます。

長さ2のタプルまたはベクターとして提供された波導インデックスは、状態 $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$ を `i = WI[1]` および `j = WI[2]` で見ることを意味します。

インデックスが提供されていない場合は基底状態が仮定されます。See [`view_waveguide`](@ref).
