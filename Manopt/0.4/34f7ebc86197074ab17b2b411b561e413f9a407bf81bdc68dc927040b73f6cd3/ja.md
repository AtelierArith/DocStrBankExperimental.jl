```
ManifoldCountObjective{E,P,O<:AbstractManifoldObjective,I<:Integer} <: AbstractDecoratedManifoldObjective{E,P}
```

任意の[`AbstractManifoldObjective`](@ref)タイプ`O`のラッパーで、目的の部分への異なる呼び出しをカウントします。

# フィールド

  * `counts` カウントされた値を保持する整数にマッピングされたシンボルの辞書
  * `objective` ラップされた目的

# サポートされているシンボル

| シンボル                         | カウントする呼び出し (含む `!` バリアント)              | コメント          |
|:---------------------------- |:-------------------------------------- |:------------- |
| `:Cost`                      | [`get_cost`](@ref)                     |               |
| `:EqualityConstraint`        | [`get_equality_constraint`](@ref)      | カウンターのベクトルが必要 |
| `:EqualityConstraints`       | [`get_equality_constraint`](@ref)      | `:`で全てを評価する場合 |
| `:GradEqualityConstraint`    | [`get_grad_equality_constraint`](@ref) | カウンターのベクトルが必要 |
| `:GradEqualityConstraints`   | [`get_grad_equality_constraint`](@ref) | `:`で全てを評価する場合 |
| `:GradInequalityConstraint`  | [`get_inequality_constraint`](@ref)    | カウンターのベクトルが必要 |
| `:GradInequalityConstraints` | [`get_inequality_constraint`](@ref)    | `:`で全てを評価する場合 |
| `:Gradient`                  | [`get_gradient`](@ref)`(M,p)`          |               |
| `:Hessian`                   | [`get_hessian`](@ref)                  |               |
| `:InequalityConstraint`      | [`get_inequality_constraint`](@ref)    | カウンターのベクトルが必要 |
| `:InequalityConstraints`     | [`get_inequality_constraint`](@ref)    | `:`で全てを評価する場合 |
| `:Preconditioner`            | [`get_preconditioner`](@ref)           |               |
| `:ProximalMap`               | [`get_proximal_map`](@ref)             |               |
| `:StochasticGradients`       | [`get_gradients`](@ref)                |               |
| `:StochasticGradient`        | [`get_gradient`](@ref)`(M, p, i)`      |               |
| `:SubGradient`               | [`get_subgradient`](@ref)              |               |
| `:SubtrahendGradient`        | [`get_subtrahend_gradient`](@ref)      |               |

# コンストラクタ

```
ManifoldCountObjective(objective::AbstractManifoldObjective, counts::Dict{Symbol, <:Integer})
```

`objective`をラップする`ManifoldCountObjective`を初期化し、カウントのセットを初期化します。

```
ManifoldCountObjective(M::AbstractManifold, objective::AbstractManifoldObjective, count::AbstractVecor{Symbol}, init=0)
```

`count`のシンボルを使用して`objective`の関数呼び出しをカウントし、すべてのエントリを`init`で初期化します。
