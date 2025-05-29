```
InteriorPointNewtonState{P,T} <: AbstractHessianSolverState
```

# フィールド

  * `λ`:           等式制約に関するラグランジュ乗数
  * `μ`:           不等式制約に関するラグランジュ乗数
  * `p::P`: マニフォールド $\mathcal M$ 上の点で、現在の反復を格納
  * `s`:           現在のスラック変数
  * `sub_problem::Union{AbstractManoptProblem, F}`:  ソルバー用の問題または閉形式の解関数を指定し、割り当て可能またはインプレースであることができます。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定するための状態。閉形式の解の場合、これは関数のタイプを示します。
  * `X`:           `p` に関する現在の勾配
  * `Y`:           `μ` に関する現在の勾配
  * `Z`:           `λ` に関する現在の勾配
  * `W`:           `s` に関する現在の勾配
  * `ρ`:           バリアパラメータ `β` をサブ問題で計算するために、直交性 `μ's/m` を格納
  * `σ`:           サブ問題でのバリアパラメータ `β` のスケーリングファクター
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `retraction_method::AbstractRetractionMethod`: 使用する再収束 $\operatorname{retr}$、[再収束に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stepsize::Stepsize`: ステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ
  * `step_problem`: ラインサーチのためのマニフォールドと目的を格納する [`AbstractManoptProblem`](@ref)
  * `step_state`: ラインサーチのための状態に反復と探索方向を格納、[`StepsizeState`](@ref)を参照

# コンストラクタ

```
InteriorPointNewtonState(
    M::AbstractManifold,
    cmo::ConstrainedManifoldObjective,
    sub_problem::Pr,
    sub_state::St;
    kwargs...
)
```

状態を初期化します。ここで、[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) と [`ConstrainedManifoldObjective`](@ref) の両方がキーワードの合理的なデフォルトを埋めるために使用されます。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `cmo`:         [`ConstrainedManifoldObjective`](@ref)
  * `sub_problem`:  ソルバー用の問題または閉形式の解関数を指定し、割り当て可能またはインプレースであることができます。
  * `sub_state`:  使用するサブソルバーを指定するための状態。閉形式の解の場合、これは関数のタイプを示します。

# キーワード引数

`m` と `n` はそれぞれ不等式と等式制約の数を示します。

  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するためのマニフォールド $\mathcal M$ 上の点
  * `μ=ones(m)`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M,p)`
  * `Y=zero(μ)`
  * `λ=zeros(n)`
  * `Z=zero(λ)`
  * `s=ones(m)`
  * `W=zero(s)`
  * `ρ=μ's/m`
  * `σ=`[`calculate_σ`](@ref)`(M, cmo, p, μ, λ, s)`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-8)`: 停止基準が満たされていることを示すファンクタ
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収束 $\operatorname{retr}$、[再収束に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `step_objective=`[`ManifoldGradientObjective`](@ref)`(`[`KKTVectorFieldNormSq`](@ref)`(cmo)`, [`KKTVectorFieldNormSqGradient`](@ref)`(cmo)`; evaluation=[`InplaceEvaluation`](@ref)`())`
  * `vector_space=`[`Rn`](@ref Manopt.Rn): 整数を与えると、ベクトル空間コンポーネント $ℝ^m,ℝ^n$ に使用されるマニフォールドを返す関数
  * `step_problem`: マニフォールド $\mathcal M × ℝ^m × ℝ^n × ℝ^m$ をラップ
  * `step_state`: ポイントと探索方向を持つ [`StepsizeState`](@ref)
  * `stepsize=`[`ArmijoLinesearch`](@ref)`()`: [`InteriorPointCentralityCondition`](@ref) を追加条件として受け入れるステップサイズを決定するための [`Stepsize`](@ref) から継承されたファンクタ

および内部的に `_step_M` と `_step_p` はステップサイズのためのマニフォールドと点です。
