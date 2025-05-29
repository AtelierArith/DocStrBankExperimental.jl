```julia
ReverseDiffAdjoint <: AbstractAdjointSensitivityAlgorithm{nothing, true, nothing}
```

ReverseDiff.jlのトレーシングベースのADを使用した離散的アジョイント感度分析の実装です。構造体の配列形式を通じてインプレース関数をサポートし、配列の構造体を通じてアウトオブプレースをサポートします。

## コンストラクタ

```julia
ReverseDiffAdjoint()
```

## SciMLProblem サポート

この`sensealg`は、アルゴリズムが`SciMLBase.isautodifferentiable`である場合、任意の`DEProblem`をサポートします。状態変数がCPUベースの`Array`型であることが必要です。
