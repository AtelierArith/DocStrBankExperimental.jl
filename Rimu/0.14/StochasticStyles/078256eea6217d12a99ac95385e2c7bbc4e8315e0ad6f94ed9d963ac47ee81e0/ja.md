このモジュールは、[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)が確率的な行列-ベクトル乗算を実行する際に使用するアルゴリズムを指定する[`StochasticStyle`](@ref)の具体的な実装を提供します。

# 実装された確率的スタイル:

  * [`StochasticStyle`](@ref): 確率的スタイルの抽象型
  * [`IsStochasticInteger`](@ref)
  * [`IsDeterministic`](@ref)
  * [`IsStochasticWithThreshold`](@ref)
  * [`IsDynamicSemistochastic`](@ref)
  * [`StyleUnknown`](@ref)

オフダイアゴナルのスポーニングは`spawning.jl`で定義されており、[`SpawningStrategy`](@ref)を設定することで制御されます。

ベクトル圧縮戦略は`compression.jl`で定義されており、[`CompressionStrategy`](@ref)を設定することで制御されます。
