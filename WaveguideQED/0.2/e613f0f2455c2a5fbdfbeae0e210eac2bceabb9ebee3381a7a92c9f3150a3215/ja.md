```
OnePhotonView(ψ::T,index::I) where {T<:SingleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

ψは単一の波導のみを含み、波導インデックスは必要ありません。`index`は[`view_waveguide`](@ref)で概説された構文に従う必要があります。
