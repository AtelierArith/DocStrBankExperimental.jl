```
SubGradientMethodState <: AbstractManoptSolverState
```

は [`subgradient_method`](@ref) ソルバーのオプション値を格納します。

# フィールド

  * `retraction_method`: 使用する再traction
  * `stepsize`:          ([`ConstantStepsize`](@ref)`(M)`) [`Stepsize`](@ref)
  * `stop`:              ([`StopAfterIteration`](@ref)`(5000)``) [`StoppingCriterion`](@ref)
  * `p`:                 (初期または現在の) アルゴリズムがある値
  * `p_star`:            最適値 (`p` のコピーで初期化されます)
  * `X`:                 (`zero_vector(M, p)`) 最後に評価された `p` における可能なサブ勾配からの現在の要素。

# コンストラクタ

```
SubGradientMethodState(M::AbstractManifold, p; kwargs...)
```

は `p_star` を除くすべてのフィールドのキーワードを持ち、`p` と同じ型を取得します。`X=` を使用して使用する接ベクトルの型を指定できます。
