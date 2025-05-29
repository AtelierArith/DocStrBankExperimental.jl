TrackState

# フィールド

  * `location::Int32`: At{Other|IP|FirstHit|LastHit|Calorimeter|Vertex}|LastLocationで使用
  * `D0::Float32`: 横方向インパクトパラメータ
  * `phi::Float32`: 方位角
  * `omega::Float32`: トラックの符号付き曲率 [1/mm]。
  * `Z0::Float32`: 縦方向インパクトパラメータ
  * `tanLambda::Float32`: lambdaはr-zにおけるトラックの傾斜角
  * `time::Float32`: このトラックステートにおけるトラックの時間
  * `referencePoint::Vector3f`: トラックパラメータの基準点、例えばIPでの原点、または最初/最後のヒットの位置、またはカロリメータへのエントリーポイント。[mm]
  * `covMatrix::SVector{21,Float32}`: トラックパラメータの下三角共分散行列。パラメータの順序はd0、phi、omega、z0、tan(lambda)、timeです。配列は行優先で行列をフラット化したものです。
