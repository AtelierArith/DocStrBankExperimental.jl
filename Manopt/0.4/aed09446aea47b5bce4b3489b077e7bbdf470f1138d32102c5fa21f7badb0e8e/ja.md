```
DifferenceOfConvexProximalState{Type} <: AbstractSubProblemSolverState
```

アルゴリズムの現在の状態と形式を格納するための構造体です。`subproblem`の実現に応じて、2つの形式があります。

# フィールド

  * `inverse_retraction_method`: (`default_inverse_retraction_method(M)`) Frank Wolfe内で使用する逆リトラクション法。
  * `retraction_method`:         (`default_retraction_method(M)`) リトラクションの種類
  * `p`, `q`, `r`:               現在の反復、勾配ステップ、およびプロキシであり、それぞれの型は`p`を初期化することで設定されます。
  * `stepsize`:                  ([`ConstantStepsize`](@ref)`(1.0)`) 修正されたアルゴリズムを実行するための[`Stepsize`](@ref)関数（実験的）
  * `stop`:                      ([`StopWhenChangeLess`](@ref)`(1e-8)`) [`StoppingCriterion`](@ref)
  * `X`, `Y`:                    (`zero_vector(M,p)`) 現在の勾配と降下方向であり、それぞれの共通の型はキーワード`X`によって設定されます。
  * `sub_problem`:               [`AbstractManoptProblem`](@ref)問題または関数`(M, p, X) -> q`または`(M, q, p, X)`の形式で、サブ問題の閉じた形式の解。
  * `sub_state`:                 サブソルバーのための[`AbstractManoptSolverState`](@ref)または、サブ問題が関数として提供される場合の[`AbstractEvaluationType`](@ref)

# コンストラクタ

```
DifferenceOfConvexProximalState(M, p; kwargs...)
```

## キーワード引数

  * `X`, `retraction_method`, `inverse_retraction_method`, `stepsize` 対応するフィールドのため
  * `stoppping_criterion` [`StoppingCriterion`](@ref)のため
