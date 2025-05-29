```
trace(shadow::DenseShadow)
```

`DenseShadow`オブジェクトのトレースを計算します。

# 引数

  * `shadow::DenseShadow`: トレースを計算する`DenseShadow`オブジェクト。

# 戻り値

シャドウのトレースを`Float64`または`ComplexF64`として返します。

# 注意事項

  * この関数は、シャドウのITensorの`ξ`および`ξ'`インデックスを収束させます。
