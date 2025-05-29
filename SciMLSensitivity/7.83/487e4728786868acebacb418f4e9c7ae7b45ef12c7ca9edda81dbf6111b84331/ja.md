```julia
TrackerAdjoint <: AbstractAdjointSensitivityAlgorithm{nothing, true, nothing}
```

Tracker.jlのトレーシングベースのADを使用した離散アジョイント感度分析の実装です。構造体の配列形式を通じてインプレース関数をサポートし、配列の構造体を通じてアウトオブプレースをサポートします。

## コンストラクタ

```julia
TrackerAdjoint()
```

## SciMLProblem サポート

この`sensealg`は、アルゴリズムが`SciMLBase.isautodifferentiable`である限り、任意の`DEProblem`をサポートします。`u0`のための限られたサブセットの`AbstractArray`型（`CuArrays`を含む）と互換性があります。

!!! warn
    TrackerAdjointは、ヤコビアンのために前方モード自動微分を使用する剛性ODEソルバーと互換性がありません。したがって、例えば`TRBDF2()`はエラーになります。代わりに、`autodiff=false`を使用してください。すなわち、`TRBDF2(autodiff=false)`です。これにより、ヤコビアン構築の前方モード自動微分が削除されますが、逆モードADの使用は維持されるため、パフォーマンスはほぼ同じままですが、ヤコビアンの精度が低下する可能性があり、より多くのステップが必要になることがあります。

