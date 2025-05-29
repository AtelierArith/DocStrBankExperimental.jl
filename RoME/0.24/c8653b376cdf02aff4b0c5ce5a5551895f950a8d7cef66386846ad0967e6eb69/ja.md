```julia
struct Pose3 <: DistributedFactorGraphs.InferenceVariable
```

Pose3は現在、3つのユークリッド変換と3つの円形回転のオイラー角のメカニズムです。

## 将来:

  * 正しい非オイラー角のオンマニホールド操作のためのAMP3Dに関する作業中。
  * TODO AMPのアップグレードは、3DからQuat/SE3/SP3への解決を目指しています - 現在のオイラー角は置き換えられます。
