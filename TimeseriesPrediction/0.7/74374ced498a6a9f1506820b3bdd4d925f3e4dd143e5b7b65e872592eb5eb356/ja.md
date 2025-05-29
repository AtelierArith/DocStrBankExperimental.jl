```
reconstruct(s::AbstractArray{<:AbstractArray{T,Φ}}, em)
```

`Vector`の`AbstractArray`状態で表される空間時系列`s`を、[`AbstractSpatialEmbedding`](@ref)型の埋め込み構造体`em`を使用して再構成します。

各行が再構成された状態であり、各状態への線形インデックスを通じて最初に順序付けられ、その後時間が増加する形で、`Dataset`（`DelayEmbeddings`から）として再構成を返します。
