```
Future{<:RasterDataSet,<:CMIPphase,<:ClimateModel,<:ClimateScenario}
```

データセット、フェーズ、モデル、シナリオで指定された将来の気候データセット。

## 型パラメータ

#### `RasterDataSet`

現在、[`BioClim`](@ref) と [`Climate`](@ref) が [`CHELSA`](@ref) データソースに対して実装されています。

#### `CMIPphase`

[`CMIP5`](@ref) または [`CMIP6`](@ref) のいずれかです。

#### `ClimateModel`

気候モデルは以下から選択できます：

``for`CMIP5`;

``for`CMIP6`;"

#### `ClimateScenario`

CMIP5の気候シナリオはすべて [`RepresentativeConcentrationPathway`](@ref) であり、以下から選択できます：`RCP26`, `RCP45`, `RCP60`, `RCP85`

CMIP6の気候シナリオはすべて [`SharedSocioeconomicPathway`](@ref) であり、以下から選択できます：`SSP126`, `SSP245`, `SSP370`, `SSP585`

ただし、すべての気候シナリオがすべてのモデルで利用できるわけではないことに注意してください。

## 例

```jldoctest future
using RasterDataSources
dataset = Future{BioClim, CMIP5, BNUESM, RCP45}
# output
Future{BioClim, CMIP5, BNUESM, RCP45}
```

現在、`Future` は `CHELSA` のみで実装されています。

```jldoctest future
datasource = CHELSA{Future{BioClim, CMIP5, BNUESM, RCP45}}
```
