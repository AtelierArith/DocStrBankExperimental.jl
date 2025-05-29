```
DensityRatioValidation(k; [options])
```

密度比検証は、最初に密度比推定を使用して重みを取得し、その後 `k`-分割重み付き交差検証に使用されます。

## オプション

  * `shuffle`   - 折りたたむ前にデータをシャッフルする（デフォルトは `true`）
  * `estimator` - 密度比推定器（デフォルトは `LSIF()`）
  * `optlib`    - 最適化ライブラリ（デフォルトは `default_optlib(estimator)`）
  * `lambda`    - 密度比の指数（デフォルトは `1.0`）
  * `loss`      - 損失関数の辞書（デフォルトは `Dict()`）

サポートされている推定器のリストについては、[DensityRatioEstimation.jl](https://github.com/JuliaEarth/DensityRatioEstimation.jl)をご覧ください。

## 参考文献

  * Hoffimann et al. 2020. [Geostatistical Learning: Challenges and Opportunities](https://arxiv.org/abs/2102.08791)
