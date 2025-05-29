```
DifferenceOfConvexProximalState{P, T, Pr, St, S<:Stepsize, SC<:StoppingCriterion, RTR<:AbstractRetractionMethod, ITR<:AbstractInverseRetractionMethod}
    <: AbstractSubProblemSolverState
```

アルゴリズムの現在の状態と形式を格納するための構造体です。`subproblem`の実現に応じて、2つの形式があります。

# フィールド

  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆再traction $\operatorname{retr}^{-1}$、[再tractionとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `q::P`: 勾配ステップを格納する多様体 $\mathcal M$ 上の点
  * `r::P`: 近接写像の結果を格納する多様体 $\mathcal M$ 上の点
  * `stepsize::Stepsize`: ステップサイズを決定するための[`Stepsize`](@ref)から継承したファンクタ
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `X`, `Y`: 現在の勾配と降下方向、それぞれの共通型はキーワード `X` によって設定されます
  * `sub_problem::Union{AbstractManoptProblem, F}`: ソルバーのための問題または閉じた形式の解関数を指定します。これは割り当て可能またはインプレースです。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定するための状態。閉じた形式の解の場合、これは関数の型を示します。

# コンストラクタ

```
DifferenceOfConvexProximalState(M::AbstractManifold, sub_problem, sub_state; kwargs...)
```

凸の差の近接点状態を構築します。

```
DifferenceOfConvexProximalState(M::AbstractManifold, sub_problem;
    evaluation=AllocatingEvaluation(), kwargs...
```

)

凸の差の近接点状態を構築します。ここで、`sub_problem`は`evaluation`を評価の型として持つ閉じた形式の解です。

## 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `sub_problem`: ソルバーのための問題または閉じた形式の解関数を指定します。これは割り当て可能またはインプレースです。
  * `sub_state`: 使用するサブソルバーを指定するための状態。閉じた形式の解の場合、これは関数の型を示します。

# キーワード引数

  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆再traction $\operatorname{retr}^{-1}$、[再tractionとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するための多様体 $\mathcal M$ 上の点
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stepsize=`[`ConstantLength`](@ref)`()`: ステップサイズを決定するための[`Stepsize`](@ref)から継承したファンクタ
  * `stopping_criterion=`[StopWhenChangeLess`](@ref)`(1e-8)`: 停止基準が満たされていることを示すファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ での接ベクトルを指定するための接ベクトルの表現
