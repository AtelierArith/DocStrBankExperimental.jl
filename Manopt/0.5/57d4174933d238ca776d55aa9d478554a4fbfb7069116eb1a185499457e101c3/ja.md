```
AdaptiveRegularizationState{P,T} <: AbstractHessianSolverState
```

[`adaptive_regularization_with_cubics`](@ref) ソルバーのための状態。

# フィールド

  * `η1`, `η1`: 正則化パラメータを評価するための境界
  * `γ1`, `γ2`: 正則化パラメータ `σ` の縮小および拡張係数
  * `H`: 現在のヘッセ行列の評価
  * `s`: サブソルバーからの現在の解
  * `p::P`: 現在の反復を格納する多様体 $\mathcal M$ 上の点
  * `q`: モデルと ρ を評価するための候補の点
  * `X::T`: 現在の反復における勾配を格納する多様体 $\mathcal M$ 上の点 $p$ での接ベクトル
  * `s`: 接空間 $T_{p}\mathcal M$ でのモデル問題を最小化することから得られる接ベクトルステップ
  * `σ`: 現在の立方体正則化パラメータ
  * `σmin`: 立方体正則化パラメータの下限
  * `ρ_regularization`: ρ を計算するための正則化パラメータ。収束に近づくと、分子と分母がゼロに近づくため、ρ の計算が難しくなる。比を正則化することで、ρ は収束近くで 1 に近づく。
  * `ρ`: 実際の改善とモデル改善の現在の正則化された比。
  * `ρ_denominator`: ρ の計算から得られる分母を格納する値。この値が非正の場合に警告またはエラーを許可する。
  * `retraction_method::AbstractRetractionMethod`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `sub_problem::Union{AbstractManoptProblem, F}`: ソルバーのための問題または閉じた形式の解関数を指定します。これは割り当て可能またはインプレースである可能性があります。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定するための状態。閉じた形式の解の場合、これは関数のタイプを示します。

さらに、以下の積分フィールドが定義されています。

# コンストラクタ

```
AdaptiveRegularizationState(M, sub_problem, sub_state; kwargs...)
```

すべてのフィールドをキーワード引数として指定し、以下のデフォルトでソルバー状態を構築します。

## キーワード引数

  * `η1=0.1`
  * `η2=0.9`
  * `γ1=0.1`
  * `γ2=2.0`
  * `σ=100/manifold_dimension(M)`
  * `σmin=1e-7`
  * `ρ_regularization=1e3`
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルがその結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目になります。
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 多様体 $\mathcal M$ 上の点
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再traction $\operatorname{retr}$、[再tractionに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(100)`: 停止基準が満たされていることを示すファンクタ
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ 上の点 $p$ での接ベクトル
