```
struct LandHydrology{
    FT,
    SM <: Soil.AbstractSoilModel{FT},
    SW <: Pond.AbstractSurfaceWaterModel{FT},
} <: AbstractLandModel{FT}
```

土壌と表面水成分を持つシステムをシミュレーションするために使用される土地モデルの具体的な型です。

  * `soil`: 土壌モデル
  * `surface_water`: 表面水モデル
