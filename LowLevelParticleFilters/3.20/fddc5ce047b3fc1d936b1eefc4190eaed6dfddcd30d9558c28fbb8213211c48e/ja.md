```
predict!(ukf::UnscentedKalmanFilter, u, p = parameters(ukf), t::Real = index(ukf) * ukf.Ts; R1 = get_mat(ukf.R1, ukf.x, u, p, t), reject, mean, cov, dynamics)
```

[`UnscentedKalmanFilter`](@ref) の予測ステップでは、ユーザーが `R1` および reject、mean、cov、dynamics のいずれかの関数をオーバーライドすることができます。

# 引数:

  * `u`: 入力
  * `p`: パラメータ
  * `t`: 現在の時間
  * `R1`: 動的ノイズ共分散行列、または共分散行列を返す関数。
  * `reject`: シグマ点を受け入れるべきかどうかを判断する `true` を返す関数。
  * `mean`: 状態シグマ点の平均を計算する関数。
  * `cov`: 状態シグマ点の共分散を計算する関数。
