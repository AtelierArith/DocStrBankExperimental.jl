```julia
accumulateFactorMeans(dfg, fctsyms; solveKey)

```

バイナリ因子のチェーンを蓄積します–-事前から始まる可能性がある–-パラメトリック平均値のみとして。

ノート

  * ツリー推論中には使用されません。
  * 期待される使用法は、因子と推定値のユーザー分析です。
  * リアルタイムのデッドレコニングチェーン予測。
  * 座標として平均値を返します。

開発ノート

  * TODO [`approxConvBelief`](@ref) と統合する
  * TODO [`solveParametricConditionals`](@ref) と比較して統合する
  * TODO [`solveFactorParametric`](@ref) と比較して統合する

関連:

[`approxConvBelief`](@ref), [`solveFactorParametric`](@ref), `RoME.MutablePose2Pose2Gaussian`
