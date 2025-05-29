```
AxisymmetricOpticalSystem{T,C<:CSGOpticalSystem{T}} <: AbstractOpticalSystem{T}
```

レンズ要素と画像検出器を持つ光学系で、処方データを含む `DataFrame` から作成されます。

これらのタグは列に対してサポートされています: `:Radius`, `:SemiDiameter`, `:SurfaceType`, `:Thickness`, `:Conic`, `:Parameters`, `:Reflectance`, `:Material`。

これらのタグは `SurfaceType` 列のエントリに対してサポートされています: `Object`, `Image`, `Stop`。`Image` 行は `DataFrame` の最後の行であると仮定します。

実際には [`CSGOpticalSystem`](@ref) が自動的に生成され、このシステム内に保存されます。

```julia
AxisymmetricOpticalSystem{T}(
    prescription::DataFrame,
    detectorpixelsx = 1000,
    detectorpixelsy:: = 1000,
    ::Type{D} = Float32;
    temperature = AGFFileReader.TEMP_REF,
    pressure = AGFFileReader.PRESSURE_REF
)
```
