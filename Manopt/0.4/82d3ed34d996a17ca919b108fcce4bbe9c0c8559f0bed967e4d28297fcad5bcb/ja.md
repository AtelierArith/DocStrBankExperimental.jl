```
FrankWolfeState <: AbstractManoptSolverState
```

[`Frank_Wolfe_method`](@ref) の現在の状態を保存するための構造体です。

`subproblem` の実現に応じて、2つの形式があります。

# フィールド

  * `p`:                         現在の反復点、マニフォールド上の点
  * `X`:                         現在の勾配 $\operatorname{grad} F(p)$、`p` に対する接ベクトル。
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, typeof(p))`) Frank Wolfe 内で使用する逆引き戻し法。
  * `sub_problem`:               [`AbstractManoptProblem`](@ref) 問題または関数 `(M, p, X) -> q` または `(M, q, p, X)` の形式で、サブ問題の閉じた形の解。
  * `sub_state`:                 サブソルバーのための [`AbstractManoptSolverState`](@ref) または、サブ問題が関数として提供される場合の [`AbstractEvaluationType`](@ref)。
  * `stop`:                      ([`StopAfterIteration`](@ref)`(200) |`[`StopWhenGradientNormLess`](@ref)`(1.0e-6)`) [`StoppingCriterion`](@ref)。
  * `stepsize`:                  ([`DecreasingStepsize`](@ref)`(; length=2.0, shift=2)`) $s_k$ はデフォルトで $s_k = \frac{2}{k+2}$ に設定されています。
  * `retraction_method`:         (`default_retraction_method(M, typeof(p))`) Frank-Wolfe 内で使用する引き戻し法。

サブタスクには、次の方法で解決する必要があります。

$$
   \operatorname*{arg\,min}_{q ∈ C} ⟨\operatorname{grad} f(p_k), \log_{p_k}q⟩.
$$

# コンストラクタ

```
FrankWolfeState(M, p, X, sub_problem, sub_state)
```

ここで、残りのフィールドはキーワード引数です。
