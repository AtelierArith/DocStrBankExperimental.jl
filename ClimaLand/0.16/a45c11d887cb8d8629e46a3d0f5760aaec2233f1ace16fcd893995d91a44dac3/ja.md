```
struct SoilSnowModel{
    FT,
    SnM <: Snow.SnowModel{FT},
    SoM <: Soil.EnergyHydrology{FT},
} <: AbstractLandModel{FT}
    "使用する雪モデル"
    snow::SnM
    "使用する土壌モデル"
    soil::SoM
end
```

雪と土壌（および最終的には河川）を持つシステムをシミュレートするために使用される具体的な土地モデルの型です。

  * `snow`: 使用する雪モデル
  * `soil`: 使用する土壌モデル
