```
boundary_vars(::MoistureStateBC, ::ClimaLand.TopBoundary)
```

MoistureStateBCの上端境界に対する`boundary_vars`メソッドの拡張です。

これらの変数は`boundary_flux!`内でその場で更新されます。
