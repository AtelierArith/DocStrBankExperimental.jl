```
boundary_vars(::RichardsAtmosDrivenFluxBC{<:PrescribedPrecipitation,
                                          <:Runoff.AbstractRunoffModel,
                                          }, ::ClimaLand.TopBoundary)
```

`boundary_vars` メソッドの RichardsAtmosDrivenFluxBC と流出の拡張です。

これらの変数は `boundary_flux!` でインプレースで更新されます。
