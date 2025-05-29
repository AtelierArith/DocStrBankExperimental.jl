プロジェクターのための抽象スーパークラスで、`dot` 積において DVec またはベクトルの代わりに使用されます。実装されたサブタイプ：

  * [`UniformProjector`](@ref)
  * [`NormProjector`](@ref)
  * [`Norm2Projector`](@ref)
  * [`Norm1ProjectorPPop`](@ref)

プロジェクターの使用については、[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem) の [`PostStepStrategy`](@ref Main.PostStepStrategy) も参照してください。

## インターフェース

`LinearAlgebra.dot(projector, v)` のメソッドを定義します。
