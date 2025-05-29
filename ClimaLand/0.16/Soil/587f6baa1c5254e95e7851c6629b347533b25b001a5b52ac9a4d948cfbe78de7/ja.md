```
boundary_vars(::AtmosDrivenFluxBC, ::ClimaLand.TopBoundary)
```

AtmosDrivenFluxBCのための`boundary_vars`メソッドの拡張です。これにより、表面条件（SHF、LHF、蒸発、および抵抗）とネット放射が補助変数に追加されます。

これらの変数は`soil_boundary_fluxes!`内でインプレースで更新されます。
