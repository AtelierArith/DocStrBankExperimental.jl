```
InstantRemineralisationSediment(grid;
                                sinking_tracers = (:P, :D), 
                                remineralisation_reciever = :N,
                                burial_efficiency_constant1 = 0.013,
                                burial_efficiency_constant2 = 0.53,
                                burial_efficiency_half_saturation = 7.0 / 6.56,
                                kwargs...)
```

Return a single-layer instant remineralisation sediment model where the `sinking_tracers` are instantly remineralised and returned to `remineralisation_reciever` with a small fraction permanently buried with efficiency:

e = a + b * f / (k + f)²

where `a` is `burial_efficiency_constant1`, `b` is `burial_efficiency_constant2`, and  `k` is the `burial_efficiency_half_saturation`.

`kwargs...` are `BiogeochemicalSediment` key word arguments.

# Example

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
