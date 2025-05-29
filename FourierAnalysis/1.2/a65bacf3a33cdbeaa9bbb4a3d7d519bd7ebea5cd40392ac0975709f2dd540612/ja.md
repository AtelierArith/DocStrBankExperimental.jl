```julia
function isNonLinear(𝒀::Union{FDobjectsVector, TFobjectsVector})
```

すべてのオブジェクトが非線形である場合はtrueを返します。定義により、[Spectra](@ref)および[ TFAmplitude](@ref)オブジェクトは線形です。[CrossSpectra](@ref)、[Coherence](@ref)、[TFAnalyticSignal](@ref)、および[TFPhase](@ref)オブジェクトは線形または非線形である可能性があります。

**参照**：[FDobjectsVector](@ref)、[TFobjectsVector](@ref)。
