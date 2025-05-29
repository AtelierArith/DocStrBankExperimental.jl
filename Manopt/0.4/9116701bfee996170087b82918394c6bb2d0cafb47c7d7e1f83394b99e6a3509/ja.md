```
DifferenceOfConvexState{Pr,St,P,T,SC<:StoppingCriterion} <:
           AbstractManoptSolverState
```

[`difference_of_convex_algorithm`](@ref) の現在の状態を格納する構造体です。`subproblem` の実現に応じて2つの形式があります。

# フィールド

  * `p`           現在の反復点、マニフォールド上の点
  * `X`           現在のサブグラディエント、`p` への接ベクトル
  * `sub_problem` サブソルバーのための問題
  * `sub_state`   サブ問題の状態
  * `stop`        停止するタイミングを示す [`StoppingCriterion`](@ref) から継承されたファンクタ

サブタスクを解決するために必要なメソッドは次の通りです。

$$
    \operatorname*{argmin}_{q∈\mathcal M}\ g(p) - ⟨X, \log_p q⟩
$$

問題とオプションに加えて、サブタスクの閉形式解を示すために関数と [`AbstractEvaluationType`](@ref) をそれぞれ提供することもできます。

# コンストラクタ

```
DifferenceOfConvexState(M, p, sub_problem, sub_state; kwargs...)
DifferenceOfConvexState(M, p, sub_solver; evaluation=InplaceEvaluation(), kwargs...)
```

[`AbstractManoptProblem`](@ref) `sub_problem` と [`AbstractManoptSolverState`](@ref) `sub_state` から与えられた Manopt のソルバーを使用して状態を生成するか、関数が `(M, p, X) -> q` または `(M, q, p, X) -> q` の形式であることが期待されるサブ問題の閉形式解 `sub_solver` を使用して状態を生成します。デフォルトでは、その [`AbstractEvaluationType`](@ref) `evaluation` は `q` のインプレースです。ここで渡される要素は、現在の反復点 `p` と `h` のサブグラディエント `X` です。

## さらなるキーワード引数

  * `initial_vector=zero_vector` (`zero_vectoir(M,p)`) 内部勾配接ベクトルを初期化する方法
  * `stopping_criterion`         [`StopAfterIteration`](@ref)`(200)` 停止基準
