```julia
partial_trace(
    M::Array{Array{T, 2}, 1},
    ed::KeldyshED.EDCore,
    target_soi::KeldyshED.Hilbert.SetOfIndices
) -> Union{Array{Float64, 3}, Matrix}

```

ブロック対角行列 `M` の部分トレースを計算します。

行列はフォック状態基底で書かれていることが期待されます。結果として得られる縮小行列は、[`set of indices`](@ref KeldyshED.Hilbert.SetOfIndices) `target_soi` によって生成されるすべてのフェルミオンフォック状態によって張られる [`Hilbert space`](@ref KeldyshED.Hilbert.FullHilbertSpace) で作用します。
