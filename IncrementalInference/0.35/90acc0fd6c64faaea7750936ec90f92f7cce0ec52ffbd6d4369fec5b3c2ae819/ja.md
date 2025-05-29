```julia
solveFactorParametric(
    dfg,
    fct,
    srcsym_vals,
    trgsym;
    solveKey,
    evaltmpkw...
)

```

ファクターチェーンに沿ってパラメトリック推定を伝播させるためのヘルパー関数。この関数は、変数の値を座標として受け取り、返します。

ノート

  * MM-iSAM推論中には使用されません。
  * 期待される使用法は、ファクターと推定のユーザー分析です。
  * リアルタイムデッドレコニングチェーン予測。
  * DRTによって使用されるパラメトリックバイナリファクタユーティリティ関数

開発ノート

  * TODO 型の安定性を確保する、現時点ではおそらく`Any`型を返す。
  * TODO MeanMaxPPEは現在座標として保存されており、高速計算を複雑にしている。

関連: [`getMeasurementParametric`](@ref), [`approxConvBelief`](@ref), [`MutablePose2Pose2Gaussian`](@ref)
