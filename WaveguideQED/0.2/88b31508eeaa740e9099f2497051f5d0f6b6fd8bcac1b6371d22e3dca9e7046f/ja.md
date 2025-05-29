```
TwoPhotonView(ψ::T,WI::F,index::I)  where {T<:MultipleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}},F<:Union{Vector{Int64},Tuple{Vararg{Int64}}}}
```

状態 `ψ` は複数の波導を含みます。

波導インデックスは長さ2のタプルまたはベクターとして提供され、状態 $\int_{t_0}^{t_{end}} dt' \int_{t_0}^{t_{end}} dt  \xi(t,t') w_{\mathrm{i}}^\dagger(t)w_{\mathrm{i}}^\dagger(t') |\emptyset \rangle$ を `i = WI[1]` および `j = WI[2]` で見ることを意味します。

インデックスは [`view_waveguide`](@ref) で強調表示された構文に従う必要があります。
