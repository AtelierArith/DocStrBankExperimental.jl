```
OnePhotonView(ψ::T,WI::Int,index::I) where {T<:MultipleWaveguideKet,I<:Union{Vector{Any},Vector{Int64},Tuple{Vararg{Union{Int64,Colon}}}}}
```

ψは複数の波導のみを含み、波導インデックス`WI`が必要です。`index`は[`view_waveguide`](@ref)で概説された構文に従う必要があります。
