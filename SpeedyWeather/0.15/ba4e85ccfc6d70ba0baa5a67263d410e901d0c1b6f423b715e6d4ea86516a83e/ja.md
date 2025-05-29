バロトロピックまたは浅水モデルの強制項で、Galewsky（2004）の初期条件に似た理想化されたジェットストリームを、両半球に対してミラーリングしたものです。

  * `nlat::Int64`: 緯度リングの数
  * `nlayers::Int64`: 垂直層の数
  * `latitude::Any`: ジェットの緯度 [˚N]
  * `width::Any`: ジェットの幅 [˚]、デフォルト ≈ 19.29˚
  * `sigma::Any`: シグマレベル [1]、ジェットの垂直位置
  * `speed::Any`: ジェットの速度スケール [m/s]
  * `time_scale::Dates.Second`: 時間スケール [日]
  * `amplitude::Vector`: 事前計算された振幅ベクトル [m/s²]
  * `tapering::Vector`: 事前計算された垂直テーパーリング
