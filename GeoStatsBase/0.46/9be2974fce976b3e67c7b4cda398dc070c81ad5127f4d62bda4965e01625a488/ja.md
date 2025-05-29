```
DensityRatioWeighting(tdata, [vars]; [options])
```

ターゲットデータ`tdata`の変数の経験的分布に基づく密度比重み。デフォルトではすべての変数が対象。

## オプションのパラメータ

  * `estimator` - 密度比推定器（デフォルトは`LSIF()`）
  * `optlib`    - 最適化ライブラリ（デフォルトは`default_optlib(estimator)`）

### 注意事項

[DensityRatioEstimation.jl](https://github.com/JuliaML/DensityRatioEstimation.jl)からの推定器がサポートされています。
