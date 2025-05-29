```
struct SoilCanopyModel{
    FT,
    MM <: Soil.Biogeochemistry.SoilCO2Model{FT},
    SM <: Soil.EnergyHydrology{FT},
    VM <: Canopy.CanopyModel{FT},
} <: AbstractLandModel{FT}
    "使用する土壌微生物モデル"
    soilco2::MM
    "使用する土壌モデル"
    soil::SM
    "使用するキャノピーモデル"
    canopy::VM
end
```

キャノピーと土壌コンポーネントを持つシステムをシミュレートするために使用される具体的な土地モデルのタイプ。

  * `soilco2`: 使用する土壌微生物モデル
  * `soil`: 使用する土壌モデル
  * `canopy`: 使用するキャノピーモデル
