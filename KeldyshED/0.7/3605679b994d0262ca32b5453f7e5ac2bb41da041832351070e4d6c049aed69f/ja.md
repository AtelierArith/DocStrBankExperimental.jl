```julia
partial_trace(
    S::Array{GF<:Keldysh.AbstractTimeGF, 1},
    ed::KeldyshED.EDCore,
    target_soi::KeldyshED.Hilbert.SetOfIndices
) -> Any

```

ブロック対角進化演算子 `S` の部分トレースを計算します。これはフォック状態基底で書かれています。

結果として得られる縮小進化演算子は、[`set of indices`](@ref KeldyshED.Hilbert.SetOfIndices) `target_soi` によって生成されるすべてのフェルミオンフォック状態によって張られる [`Hilbert space`](@ref KeldyshED.Hilbert.FullHilbertSpace) で作用します。
