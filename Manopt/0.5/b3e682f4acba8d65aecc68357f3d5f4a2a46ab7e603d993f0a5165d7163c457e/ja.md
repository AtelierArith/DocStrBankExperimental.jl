```
mesh_adaptive_direct_search(M, f, p=rand(M); kwargs...)
mesh_adaptive_direct_search(M, mco::AbstractManifoldCostObjective, p=rand(M); kwargs..)
mesh_adaptive_direct_search!(M, f, p; kwargs...)
mesh_adaptive_direct_search!(M, mco::AbstractManifoldCostObjective, p; kwargs..)
```

メッシュ適応直接探索（MADS）アルゴリズムは、マニフォールド `M` 上の目的関数 $f: \mathcal M → ℝ$ を最小化します。このアルゴリズムは、現在の候補点 $p$ における接空間 $T_{p}\mathcal M$ に暗黙のメッシュを構築します。各反復は、探索ステップとポールステップから構成されます。

探索ステップは、暗黙のメッシュから点を選択し、$f$ の値を減少させる改善された候補解を見つけようとします。探索ステップが改善された候補解を生成できない場合、ポールステップが実行されます。これは、現在の反復の近傍における現在の暗黙のメッシュ上での局所探索から成ります。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ として実装された `(M, p) -> v`
  * `p`: マニフォールド $\mathcal M$ 上の点

# キーワード引数

  * `mesh_basis=`[`DefaultOrthonormalBasis`](@extref `ManifoldsBase.DefaultOrthonormalBasis`): メッシュを生成するための基底。この基底の座標系で各接空間においてメッシュが生成されます
  * `max_stepsize=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(M)`: 取る最大ステップサイズ。メッシュ上で生成された任意のベクトルは、この長さに短縮され、射影半径を超えないようにします。
  * `poll::`[`AbstractMeshPollFunction`](@ref)`=`[`LowerTriangularAdaptivePoll`](@ref)`(M, copy(M,p))`: 使用するポール関数。`mesh_basis`（`basis`として）、`retraction_method`、および `vector_transport_method` がこのデフォルトにも渡されます。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション $\operatorname{retr}$、詳細は [リトラクションに関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。
  * `scale_mesh=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(M) / 4`: メッシュの初期スケーリング
  * `search::`[`AbstractMeshSearchFunction`](@ref)`=`[`DefaultMeshAdaptiveDirectSearch`](@ref)`(M, copy(M,p))`: 使用する探索関数。`retraction_method` もこのデフォルトに渡されます。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenPollSizeLess`](@ref)`(1e-10)`: 停止基準が満たされていることを示すファンクタ
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は [ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`) を参照してください。
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: マニフォールド $\mathcal M$ 上の点 $p$ における接ベクトル

他のすべてのキーワード引数は、状態デコレーター用の [`decorate_state!`](@ref) または目的デコレーター用の [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、特に `return_state=` キーワードについての詳細は [`get_solver_return`](@ref) を参照してください。
