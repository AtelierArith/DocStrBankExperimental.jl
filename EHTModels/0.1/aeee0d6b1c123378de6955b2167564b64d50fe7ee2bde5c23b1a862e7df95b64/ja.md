```julia
abstract type GeometricModel <: EHTModels.AbstractModel
```

幾何モデルであることを定義する型です。これらは通常、原始的なモデルであり、通常はフーリエおよび画像領域で解析的です。その結果、ユーザーは以下のメソッドのみを実装する必要があります。

  * `visibility_point`
  * `intensity_point`
  * `radialextent`

幾何モデルが**解析的**でない場合、非解析モデルのために[`Comrade.AbstractModel`](@ref)に記載されている通常のメソッドを実装する必要があることに注意してください。
