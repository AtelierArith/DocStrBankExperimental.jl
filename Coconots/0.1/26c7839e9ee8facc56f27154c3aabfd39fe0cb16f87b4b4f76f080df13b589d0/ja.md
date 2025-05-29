```
compute_random_pacfs(cocoReg_fit, lags, n_bootstrap=400, n_burn_in=200, pacfs=Array{Float64}(undef, n_bootstrap, length(lags)))
```

適合したモデルから新しいデータセットをシミュレーションすることによって、ブートストラップされた部分自己相関係数を生成します。各ブートストラップ反復ごとに、`cocoSim`を使用してデータをシミュレートし、指定されたラグに対してPACFを計算します。

# 引数

  * `cocoReg_fit`: 適合したモデルのパラメータと観測データを含む辞書。
  * `lags`: PACFを計算するラグ値のベクトル。
  * `n_bootstrap` (オプション): ブートストラップサンプルの数（デフォルトは400）。
  * `n_burn_in` (オプション): シミュレーション中に破棄するバンインサンプルの数（デフォルトは200）。
  * `pacfs` (オプション): 各ブートストラップサンプルからのPACF値を格納するための事前割り当てされた行列。

# 戻り値

次元が`(n_bootstrap, length(lags))`のブートストラップされたPACF値の行列。
