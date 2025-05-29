```
struct LandSoilBiogeochemistry{
    FT,
    SEH <: Soil.EnergyHydrology{FT},
    SB <: Soil.Biogeochemistry.SoilCO2Model{FT},
} <: AbstractLandModel{FT}
```

土壌エネルギー、水文学、および生物地球化学コンポーネントを持つシステムをシミュレーションするために使用される土地モデルの具体的な型です。

  * `soil`: 土壌モデル
  * `soilco2`: 生化学モデル
