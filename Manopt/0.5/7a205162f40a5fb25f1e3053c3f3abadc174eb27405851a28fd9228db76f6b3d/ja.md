```
DifferenceOfConvexState{Pr,St,P,T,SC<:StoppingCriterion} <:
           AbstractManoptSolverState
```

現在の状態を格納する構造体であり、[`difference_of_convex_algorithm`](@ref)の実現に応じて2つの形式があります。

# フィールド

  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `X::T`: 現在の反復におけるサブグラディエントを格納する多様体 $\mathcal M$ 上の点 $p$ における接ベクトル
  * `sub_problem::Union{AbstractManoptProblem, F}`: ソルバー用の問題または、割り当て可能またはインプレースの閉形式解関数を指定します。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定する状態。閉形式解の場合、これは関数の型を示します。
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ

サブタスクは、次の方法を解決することから成ります。

$$
    \operatorname*{arg\,min}_{q∈\mathcal M}\ g(p) - ⟨X, \log_p q⟩
$$

問題と状態に加えて、サブタスクの閉形式解を示すために関数と[`AbstractEvaluationType`](@ref)を提供することもできます。

# コンストラクタ

```
DifferenceOfConvexState(M, sub_problem, sub_state; kwargs...)
DifferenceOfConvexState(M, sub_solver; evaluation=InplaceEvaluation(), kwargs...)
```

状態を生成するには、[`AbstractManoptProblem`](@ref) `sub_problem` と [`AbstractManoptSolverState`](@ref) `sub_state` からManoptのソルバーを使用するか、サブ問題のための閉形式解 `sub_solver` を使用します。この関数は `(M, p, X) -> q` または `(M, q, p, X) -> q` の形式であることが期待され、デフォルトではその[`AbstractEvaluationType`](@ref) `evaluation` は `q` のインプレースです。ここで渡される要素は、現在の反復 `p` と `h` のサブグラディエント `X` です。

## その他のキーワード引数

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定する多様体 $\mathcal M$ 上の点
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`: 停止基準が満たされていることを示すファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 接ベクトルの表現を指定するための多様体 $\mathcal M$ 上の点 $p$ における接ベクトル
