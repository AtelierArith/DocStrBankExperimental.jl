```
push!(::ContinuousHistogram, ::Tuple{Number, Number})
push!(::ContinuousHistogram, ::Measurement)
push!(::ContinuousHistogram, ::AbstractVector)
push!(::ContinuousHistogram, ::Vector{Measurement})
```

`Base` のオーバーロードは、[`ContinuousHistogram`](@ref) に新しい値-エラーペアを導入します。この関数は、わずかなオーバーヘッドで [`_update_moments!`](@ref) も行います。

!!! note
    `AbstractVector` のディスパッチは、実際には `Vector{Tuple{Number, Number}}` のためだけに意図されています。後者にはサブタイプが含まれていません。

