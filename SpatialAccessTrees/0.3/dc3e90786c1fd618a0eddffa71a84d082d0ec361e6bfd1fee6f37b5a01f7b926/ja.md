```
BeamSearchMultiSat(sat::Vector{SatType}; bsize=8, Δ=1f0) where {SatType<:Sat}
```

マルチSAT配列にビームサーチを適用します。特定の目的のためにインデックスを調整するには、[`optimize!`](@ref)を参照してください。
