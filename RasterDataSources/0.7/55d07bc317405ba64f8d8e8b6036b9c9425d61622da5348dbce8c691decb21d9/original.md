```
Future{<:RasterDataSet,<:CMIPphase,<:ClimateModel,<:ClimateScenario}
```

Future climate datasets specified with a dataset, phase, model, and scenario.

## Type Parameters

#### `RasterDataSet`

Currently [`BioClim`](@ref) and [`Climate`](@ref) are implemented for the [`CHELSA`](@ref) data source.

#### `CMIPphase`

Can be either [`CMIP5`](@ref) or [`CMIP6`](@ref).

#### `ClimateModel`

Climate models can be chosen from: 

``for`CMIP5`;

``for`CMIP6`;"

#### `ClimateScenario`

CMIP5 Climate scenarios are all [`RepresentativeConcentrationPathway`](@ref) and can be chosen from: `RCP26`, `RCP45`, `RCP60`, `RCP85`

CMIP6 Climate scenarios are all [`SharedSocioeconomicPathway`](@ref) and can be chosen from: `SSP126`, `SSP245`, `SSP370`, `SSP585`

However, note that not all climate scenarios are available for all models.

## Example

```jldoctest future
using RasterDataSources
dataset = Future{BioClim, CMIP5, BNUESM, RCP45}
# output
Future{BioClim, CMIP5, BNUESM, RCP45}
```

Currently `Future` is only implented for `CHELSA`

```jldoctest future
datasource = CHELSA{Future{BioClim, CMIP5, BNUESM, RCP45}}
```
