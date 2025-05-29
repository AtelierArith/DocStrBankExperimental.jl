```
correct!(ukf::UnscentedKalmanFilter{IPD, IPM, AUGD, AUGM}, u, y, p = parameters(ukf), t::Real = index(ukf) * ukf.Ts; R2 = get_mat(ukf.R2, ukf.x, u, p, t), mean, cross_cov, innovation)
```

[`UnscentedKalmanFilter`](@ref) の補正ステップでは、ユーザーが `R2`、`mean`、`cross_cov`、`innovation` をオーバーライドすることができます。

# 引数:

  * `u`: 入力
  * `y`: 測定値
  * `p`: パラメータ
  * `t`: 現在の時間
  * `R2`: 測定ノイズ共分散行列、または共分散行列を返す関数 `(x,u,p,t)->R2`。
  * `mean`: 出力シグマ点の加重平均を計算する関数。
  * `cross_cov`: 状態と出力シグマ点の加重クロス共分散を計算する関数。
  * `innovation`: 測定された出力と予測された出力の間のイノベーションを計算する関数。

# 拡張ヘルプ

異なるセンサーのために別々の測定更新を行うには、[ドキュメントの「測定モデル」](@ref measurement_models)を参照してください。
