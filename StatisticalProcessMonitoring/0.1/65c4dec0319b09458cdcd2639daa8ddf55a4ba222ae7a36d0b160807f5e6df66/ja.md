```
NEWMA
```

プロファイルを監視するための非パラメトリック指数加重移動平均統計量。

# フィールド

  * `λ::Float64`: EWMAスムージング定数。0と1の間でなければならない。
  * `value::Float64`: NEWMA統計量の現在の値。
  * `σ::Float64`: 誤差項の標準偏差。
  * `cdf_σ::E`: 誤差項 `σ` の（推定された）累積分布関数を計算する関数。シグネチャは `cdf_σ(x::Real)`。
  * `g::F`: 推定された回帰関数オブジェクト。シグネチャ `predict(g::F, x::AbstractVector)` のメソッドを持っている必要がある。
  * `Ej::Vector{Float64}`: 現在のスムーズな観測値。

# 参考文献

Zou, C., Tsung, F., & Wang, Z. (2008). Monitoring Profiles Based on Nonparametric Regression Methods. Technometrics, 50(4), 512-526. https://doi.org/10.1198/004017008000000433
