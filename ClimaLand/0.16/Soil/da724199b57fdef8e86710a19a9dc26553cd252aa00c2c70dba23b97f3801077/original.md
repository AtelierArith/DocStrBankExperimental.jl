```
ClimaLand.get_drivers(model::RichardsModel)
```

Returns the driver variable symbols for the RichardsModel; these depend on the boundary condition type and currently only are required for the RichardsAtmosDrivenFluxBC, which is driven by a prescribed time and space varying precipitation.
