```julia
canonicalize_rref!(
    state::QuantumClifford.AbstractStabilizer,
    colindices;
    phases
) -> Tuple{QuantumClifford.AbstractStabilizer, Any}

```

一部の列に沿って安定器を（インプレースで）標準化します。

これは[`canonicalize!`](@ref)とは異なる標準形を使用します。また、[`traceout!`](@ref)での使用をより効率的にするために逆にインデックス付けを行います。`traceout!`での使用が主な応用です。

（インプレースで）修正された状態と最後のピボットのインデックスを返します。

[audenaert2005entanglement](@cite)に基づいています。

関連項目: [`canonicalize!`](@ref), [`canonicalize_gott!`](@ref)
