```
TrustRegionsState <: AbstractHessianSolverState
```

信頼領域ソルバーの状態を保存します。

# フィールド

以下のすべてのフィールド（`p`を除く）は、キーワードとして指定することで設定できます。

  * `acceptance_rate`:         （`0.1`）反復が受け入れられるかどうかを決定するための性能比の下限。
  * `max_trust_region_radius`: （`sqrt(manifold_dimension(M))`）最大信頼領域半径
  * `p`:                       （`rand(M)`がマニフォールドが提供されている場合）現在の反復
  * `project!`:                （`copyto!`）数値的安定性のための接ベクトルの射影操作を指定します。関数 `(M, Y, p, X) -> ...` が `Y` の場所で動作します。デフォルトでは、射影は行われず、`project!` に設定することで射影が有効になります。
  * `stop`:                    （[`StopAfterIteration`](@ref)`(1000) |`[`StopWhenGradientNormLess`](@ref)`(1e-6)`)
  * `randomize`:               （`false`）信頼領域の解法がランダムな接ベクトルで開始されるかどうかを示します。trueに設定すると、前処理器は使用されません。このオプションは、鞍点から脱出するためにいくつかのシナリオでtrueに設定されますが、それ以外ではあまり有効にされません。
  * `ρ_regularization`:        （`10000.0`）ゼロ除算を避けるためにモデルフィットネス $ρ$ を正則化します。
  * `sub_problem`:             [`AbstractManoptProblem`](@ref) 問題または関数 `(M, p, X) -> q` または `(M, q, p, X)` のサブ問題の閉形式解法
  * `sub_state`:               （[`TruncatedConjugateGradientState`](@ref)`(M, p, X)`)
  * `σ`:                       （`0.0` または `1e-6` `randomize` に応じて）ランダムな初期接ベクトルを作成する際のガウス標準偏差
  * `trust_region_radius`:     （`max_trust_region_radius / 8`）(初期)信頼領域半径
  * `X`:                       （`zero_vector(M,p)`）現在の勾配 `grad_f(p)` このデフォルトを使用して、内部（接ベクトル）フィールドのために割り当てる接ベクトルの型を指定します。

# 内部フィールド

  * `HX`, `HY`, `HZ`:          ``\operatorname{Hess} f(p)[\cdot]` の `X`, `Y`, `Z` の一時ストレージ（割り当てを避けるため）
  * `Y`:                       サブソルバーの解（接ベクトル）
  * `Z`:                       コーシー点（ランダムが有効な場合のみ使用）

# コンストラクタ

以下のすべてのコンストラクタは、デフォルトが括弧内に示されたフィールドをキーワード引数として持ちます。初期点 `p` が提供されない場合、`p=rand(M)` が使用されます。

```
TrustRegionsState(M, mho; kwargs...)
TrustRegionsState(M, p, mho; kwargs...)
```

サブ問題が [`DefaultManoptProblem`](@ref) に設定され、[`TrustRegionModelObjective`](@ref) を使用して解決される信頼領域の状態。言い換えれば、サブ状態は [`TruncatedConjugateGradientState`](@ref) に設定されます。

```
TrustRegionsState(M, sub_problem, sub_state; kwargs...)
TrustRegionsState(M, p, sub_problem, sub_state; kwargs...)
```

サブ問題が [`AbstractManoptProblem`](@ref) `sub_problem` と [`AbstractManoptSolverState`](@ref) `sub_state` を使用して解決される信頼領域の状態。

```
TrustRegionsState(M, f::Function; evaluation=AllocatingEvaluation, kwargs...)
TrustRegionsState(M, p, f; evaluation=AllocatingEvaluation, kwargs...)
```

サブ問題が関数 `f(M, p, Y, Δ)` によって閉形式で解決される信頼領域の状態。ここで、`p` は現在の反復、`Y` は `p` での初期接ベクトル、`Δ` は現在の信頼領域半径です。

# 参照

[`trust_regions`](@ref), [`trust_regions!`](@ref)
