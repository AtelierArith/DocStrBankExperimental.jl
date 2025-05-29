```julia
abstract type AbstractScatteringKernel{T} <: ComradeBase.AbstractModel
```

diffractive scattering kernel のための抽象 Comrade Sky Model。これらは通常、原始的なモデルであり、フーリエでは解析的ですが、画像領域では解析的ではありません。その結果、ユーザーは次のメソッドのみを実装する必要があります。

  * `visibility_point`
  * `radialextent`
