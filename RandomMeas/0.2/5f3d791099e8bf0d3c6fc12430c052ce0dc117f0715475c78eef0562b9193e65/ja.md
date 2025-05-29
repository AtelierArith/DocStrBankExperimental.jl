```
trace(shadow::FactorizedShadow)
```

`FactorizedShadow`オブジェクトのトレースを計算します。

# 引数

  * `shadow::FactorizedShadow`: トレースを計算する`FactorizedShadow`オブジェクト。

# 戻り値

シャドウのトレースを`Float64`または`ComplexF64`として返します。

# 注意事項

  * この関数は、因子化されたシャドウ内の個々のテンソルのトレースの積を計算します。
