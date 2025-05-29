```
CSGOpticalSystem{T,D<:Real,S<:Surface{T},L<:LensAssembly{T}} <: AbstractOpticalSystem{T}
```

レンズアセンブリと関連する画像を持つ検出器表面を含む光学系です。システムは指定された温度と圧力で存在することができます。

型シグネチャには2つの数値型があります。`T`型パラメータは光学系の幾何学の数値型であり、`D`型パラメータは検出器画像のピクセルの数値型です。このようにして、幾何学に`Float64`を使用することができ、高精度が重要ですが、検出器のピクセルは画像データの精度がそれほど重要でないため`Float32`にすることができます。また、波光学シミュレーションを行う場合はComplexを使用することもできます。

検出器は、[`Surface`](@ref)を実装し、[`uv`](@ref)、[`uvtopix`](@ref)、および[`onsurface`](@ref)を持つ任意のものであり、通常は[`Rectangle`](@ref)、[`Ellipse`](@ref)、または[`SphericalCap`](@ref)のいずれかです。

```julia
CSGOpticalSystem(
    assembly::LensAssembly,
    detector::Surface,
    detectorpixelsx = 1000,
    detectorpixelsy = 1000, ::Type{D} = Float32;
    temperature = AGFFileReader.TEMP_REF,
    pressure = AGFFileReader.PRESSURE_REF
)
```
