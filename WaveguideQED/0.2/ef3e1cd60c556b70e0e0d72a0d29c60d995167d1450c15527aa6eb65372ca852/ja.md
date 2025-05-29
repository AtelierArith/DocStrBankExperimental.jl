```
TwoPhotonView(ψ::T,WI1::Int,WI2::Int,index::I)  where {T<:MultipleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

状態 `ψ` は複数の波導を含みます。

2つの波導インデックスは、状態 $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$ を `i = WI1` および `j = WI2` で表示することを意味します。

インデックスは [`view_waveguide`](@ref) で強調表示された構文に従う必要があります。
