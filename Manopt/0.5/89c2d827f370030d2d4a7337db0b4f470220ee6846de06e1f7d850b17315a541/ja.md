```
TrustRegionsState <: AbstractHessianSolverState
```

信頼領域ソルバーの状態を保存します。

# フィールド

  * `acceptance_rate`:         イテレーションが受け入れられるかどうかを決定するためのパフォーマンス比の下限。
  * `HX`, `HY`, `HZ`:          ``\operatorname{Hess} f(p)[⋅]` の中間ストレージ（アロケーションを避けるため）`X`, `Y`, `Z`の
  * `max_trust_region_radius`: 最大信頼領域半径
  * `p::P`: マニフォールド $\mathcal M$ 上の現在のイテレーションを格納する点
  * `project!`:                数値的安定性のために、各イテレーションの後に接空間に投影することが可能です。この関数は `Y` のインプレースで動作する必要があります。すなわち、`(M, Y, p, X) -> Y` であり、`X` と `Y` は同じメモリである可能性があります。
  * `stop::StoppingCriterion`: 停止基準が満たされていることを示すファンクタ
  * `randomize`:               `X` がランダムベクトルで初期化されるかどうかを示す
  * `ρ_regularization`:        ゼロ除算を避けるためにモデルフィットネス $ρ$ を正則化する
  * `sub_problem::Union{AbstractManoptProblem, F}`:  ソルバー用の問題またはクローズドフォームソリューション関数を指定します。アロケーションまたはインプレースである可能性があります。
  * `sub_state::Union{AbstractManoptProblem, F}`: 使用するサブソルバーを指定する状態。クローズドフォームソリューションの場合、これは関数のタイプを示します。
  * `σ`:                       ランダム初期接ベクトルを作成する際のガウス標準偏差。このフィールドは、`randomize` が false の場合には効果がありません。
  * `trust_region_radius`: 信頼領域半径
  * `X::T`: マニフォールド $\mathcal M$ 上の点 $p$ における接ベクトル
  * `Y`:                       サブソルバーの解（接ベクトル）
  * `Z`:                       コーシー点（ランダムが有効な場合のみ使用）

# コンストラクタ

```
TrustRegionsState(M, mho::AbstractManifoldHessianObjective; kwargs...)
TrustRegionsState(M, sub_problem, sub_state; kwargs...)
TrustRegionsState(M, sub_problem; evaluation=AllocatingEvaluation(), kwargs...)
```

信頼領域状態を作成します。

  * [`AbstractManifoldHessianObjective`](@ref) `mho` が与えられた場合、デフォルトのサブソルバーとして、接空間上の問題を定義するために `mho` を使用した [`TruncatedConjugateGradientState`](@ref) が作成されます。
  * `sub_problem` と `evaluation=` キーワードが与えられた場合、サブ問題ソルバーはクローズドフォームソリューションであると仮定され、`evaluation` がサブ関数の呼び出し方法を決定します。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `sub_problem`:  ソルバー用の問題またはクローズドフォームソリューション関数を指定します。アロケーションまたはインプレースである可能性があります。
  * `sub_state`:  使用するサブソルバーを指定する状態。クローズドフォームソリューションの場合、これは関数のタイプを示します。

## キーワード引数

  * `acceptance_rate=0.1`
  * `max_trust_region_radius=sqrt(manifold_dimension(M))`
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値を指定するためのマニフォールド $\mathcal M$ 上の点
  * `project!=copyto!`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: 停止基準が満たされていることを示すファンクタ
  * `randomize=false`
  * `ρ_regularization=10000.0`
  * `θ=1.0`
  * `trust_region_radius=max_trust_region_radius / 8`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 接ベクトルの表現を指定するためのマニフォールド $\mathcal M$ 上の点 $p$ における接ベクトル

# 参照

[`trust_regions`](@ref)
