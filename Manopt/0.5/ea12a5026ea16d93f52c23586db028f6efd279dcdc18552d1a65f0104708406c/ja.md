```
FrankWolfeState <: AbstractManoptSolverState
```

[`Frank_Wolfe_method`](@ref)の現在の状態を保存するための構造体です。

`subproblem`の実現に応じて、2つの形式があります。

# フィールド

  * `p::P`: 現在の反復を保存する多様体$\mathcal M$上の点
  * `X::T`: 現在の反復における勾配を保存する多様体$\mathcal M$上の点$p$での接ベクトル
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆引き戻し$\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送$\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `sub_problem::Union{AbstractManoptProblem, F}`: ソルバー用の問題または閉形式の解関数を指定します。これは割り当て可能またはインプレースである可能性があります。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定するための状態。閉形式の解の場合、これは関数のタイプを示します。
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `stepsize::Stepsize`: ステップサイズを決定するための[`Stepsize`](@ref)から継承されたファンクタ
  * `retraction_method::AbstractRetractionMethod`: 使用する引き戻し$\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照

サブタスクには、次の方法で解決する必要があります。

$$
   \operatorname*{arg\,min}_{q ∈ C} ⟨\operatorname{grad} f(p_k), \log_{p_k}q⟩.
$$

# コンストラクタ

```
FrankWolfeState(M, sub_problem, sub_state; kwargs...)
```

フランク・ウルフ法の状態を初期化します。

FrankWolfeState(M, sub_problem; evaluation=AllocatingEvaluation(), kwargs...)

`sub_problem`が閉形式の解であり、`evaluation`が評価のタイプであるフランク・ウルフ法の状態を初期化します。

## 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体$\mathcal M$
  * `sub_problem`: ソルバー用の問題または閉形式の解関数を指定します。これは割り当て可能またはインプレースである可能性があります。
  * `sub_state`: 使用するサブソルバーを指定するための状態。閉形式の解の場合、これは関数のタイプを示します。

## キーワード引数

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定する多様体$\mathcal M$上の点
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆引き戻し$\operatorname{retr}^{-1}$、[引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し$\operatorname{retr}$、[引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: 停止基準が満たされていることを示すファンクタ
  * `stepsize=`[`default_stepsize`](@ref)`(M, FrankWolfeState)`: ステップサイズを決定するための[`Stepsize`](@ref)から継承されたファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 接ベクトルの表現を指定するために多様体$\mathcal M$上の点$p$での接ベクトル

残りのフィールドはキーワード引数です。
