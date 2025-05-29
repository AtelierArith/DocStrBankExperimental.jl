```
PathParameters
```

カスタムタイプで、フーリエスペクトルのパスパラメータを定義します。3つの他のカスタム構造体で構成されています。

  * `geometric` は `GeometricSpreadingParameters` タイプです
  * `saturation` は `NearSourceSaturationParameters` タイプです
  * `anelastic` は `AnelasticAttenuationParameters` タイプです

基本コンストラクタは次のとおりです: `PathParameters(geo::G, sat::S, ane::A) where {G<:GeometricSpreadingParameters, S<:NearSourceSaturationParameters, A<:AnelasticAttenuationParameters}`

参照: [`FourierParameters`](@ref)
