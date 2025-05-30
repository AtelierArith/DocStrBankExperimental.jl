```
InstantRemineralisationSediment(grid;
                                sinking_tracers = (:P, :D), 
                                remineralisation_reciever = :N,
                                burial_efficiency_constant1 = 0.013,
                                burial_efficiency_constant2 = 0.53,
                                burial_efficiency_half_saturation = 7.0 / 6.56,
                                kwargs...)
```

`すぐに再鉱化される堆積物モデル`を返します。ここで、`sinking_tracers`は即座に再鉱化され、`remineralisation_reciever`に戻されますが、効率的に少量が永久に埋められます：

e = a + b * f / (k + f)²

ここで、`a`は`burial_efficiency_constant1`、`b`は`burial_efficiency_constant2`、`k`は`burial_efficiency_half_saturation`です。

`kwargs...`は`BiogeochemicalSediment`のキーワード引数です。

# 例

```@example
using OceanBioME, Oceananigans

grid = RectilinearGrid(size=(3, 3, 30), extent=(10, 10, 200))

sediment_model = InstantRemineralisationSediment(grid)

biogeochemistry = NPZD(; grid, sediment_model)
```

```@example
using OceanBioME, Oceananigans

grid = RectilinearGrid(size=(3, 3, 30), extent=(10, 10, 200))

sediment_model = InstantRemineralisationSediment(grid; 
                                                 sinking_tracers = (:sPOM, :bPOM),
                                                 remineralisation_reciever = :NH₄)

biogeochemistry = LOBSTER(; grid, sediment_model)
```
