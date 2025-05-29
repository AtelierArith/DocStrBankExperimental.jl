##### 引数

  * `kn::Kalman`: モデルを指定する `Kalman`。初期値は t=1 の期間観測の事前値、すなわち $x_{1|0}$ でなければなりません。
  * `y::AbstractMatrix`: 観測データの `n x T` 行列。 `n` は1期間における観測変数の数です。各列は各期間の観測のベクトルです。

##### 戻り値

  * `x_smoothed::AbstractMatrix`: 状態の平滑化された平均の `k x T` 行列。 `k` は状態の数です。
  * `logL::Real`: すべての観測の対数尤度
  * `sigma_smoothed::AbstractArray` `k x k x T` 状態の平滑化された共分散行列の配列。
