```
boundary_var_types(::RichardsModel{FT},
                    ::RichardsAtmosDrivenFluxBC{<:PrescribedPrecipitation,
                                                <: Runoff.AbstractRunoffModel,
                                              },
                    ::ClimaLand.TopBoundary,
                    ) where {FT}
```

`boundary_var_types` メソッドの RichardsAtmosDrivenFluxBC と流出の拡張。
