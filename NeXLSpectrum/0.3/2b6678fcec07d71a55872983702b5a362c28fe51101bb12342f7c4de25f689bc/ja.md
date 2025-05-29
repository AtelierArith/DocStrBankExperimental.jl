```
block(hss::HyperSpectrum{T,N,NP}, steps::NTuple{N, Int})::HyperSpectrum{T,N,NP} where {T<:Real, N, NP}
block(hss::HyperSpectrum{T,N,NP}, step::Int) where {T<:Real, N, NP}
```

隣接するピクセルのブロックを合計することで、HyperSpectrumのサイズを減らします。たとえば、`steps=(4,4)`は、`hss`内の16のスペクトルのブロックを合計して、結果の`Hyperspectrum`内の単一のピクセルを形成します。
