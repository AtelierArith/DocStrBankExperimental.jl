```
struct LandModel{
    FT,
    MM <: Soil.Biogeochemistry.SoilCO2Model{FT},
    SM <: Soil.EnergyHydrology{FT},
    VM <: Canopy.CanopyModel{FT},
    SnM <: Snow.SnowModel{FT},
} <: AbstractLandModel{FT}
    "使用する土壌微生物モデル"
    soilco2::MM
    "使用する土壌モデル"
    soil::SM
    "使用するキャノピーモデル"
    canopy::VM
    "使用する雪モデル"
    snow::SnM
end
```

土壌、キャノピー、雪、soilco2を用いたシステムをシミュレーションするための具体的な土地モデルの型です。

  * `soilco2`: 使用する土壌微生物モデル
  * `soil`: 使用する土壌モデル
  * `canopy`: 使用するキャノピーモデル
  * `snow`: 使用する雪モデル
