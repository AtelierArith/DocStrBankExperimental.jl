```
TwoPhotonView(ψ::T,WI::Int,index::I)  where {T<:MultipleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

状態 `ψ` は複数の波導を含みます。

波導インデックス `i=WI` のみは、状態を表示することを意味します $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$。

インデックスは [`view_waveguide`](@ref) で強調表示された構文に従う必要があります。
