```
boundary_var_types(::RichardsModel{FT},
                    ::RichardsAtmosDrivenFluxBC{<:PrescribedPrecipitation,
                                                <: Runoff.AbstractRunoffModel,
                                              },
                    ::ClimaLand.TopBoundary,
                    ) where {FT}
```

An extension of the `boundary_var_types` method for RichardsAtmosDrivenFluxBC with runoff.
