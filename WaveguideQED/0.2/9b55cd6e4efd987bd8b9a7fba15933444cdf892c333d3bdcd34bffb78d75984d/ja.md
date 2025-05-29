```
TwoPhotonView(ψ::T,index::I) where {T <: SingleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

状態 `ψ` は波導が1つだけ含まれています。インデックスは [`view_waveguide`](@ref) で強調表示された構文に従う必要があります。
