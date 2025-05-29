```julia
struct RingTemplate{R<:VLBISkyModels.AbstractRadial, A<:VLBISkyModels.AbstractAzimuthal} <: VLBISkyModels.AbstractImageTemplate
```

放射状および方位角の輝度プロファイルの積を取ることでリングを形成する柔軟なリングテンプレートです。

放射プロファイルのリストは `subtypes(AbstractRadial)` によって与えられます。

方位角プロファイルのリストは `subtypes(AbstractAzimuthal)` によって与えられます。

## 例

```julia-repl
julia> rad = RadialGaussian(0.1)
julia> azi = AzimuthalUniform()
julia> ring = modify(RingTemplate(rad, azi), Stretch(10.0), Shift(1.0, 2.0))
```

## フィールド

  * `radial`: リングの放射プロファイル
  * `azimuthal`: リングの方位角プロファイル
