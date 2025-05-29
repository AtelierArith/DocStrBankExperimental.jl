```
ParticleSwarmState{P,T} <: AbstractManoptSolverState
```

粒子群最適化アルゴリズムを説明します。

# フィールド

  * `cognitive_weight`: 認知重み係数
  * `inertia`:          粒子の慣性
  * `inverse_retraction_method::AbstractInverseRetractionMethod`: 使用する逆再引き戻し $\operatorname{retr}^{-1}$、詳細は[再引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `retraction_method::AbstractRetractionMethod`: 使用する再引き戻し $\operatorname{retr}$、詳細は[再引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `social_weight`:    社会的重み係数
  * `stop::StoppingCriterion`: 停止基準が満たされたことを示すファンクタ
  * `vector_transport_method::AbstractVectorTransportMethodP`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照
  * `velocity`:         粒子の速度を表す接ベクトルの集合（型 `AbstractVector{T}`）

# 内部および一時的フィールド

  * `cognitive_vector`: `cognitive_weight` に関連する接ベクトルの一時的ストレージ
  * `p::P`: 全粒子が訪れた最良の点を格納する多様体 $\mathcal M$ 上の点
  * `positional_best`:  各粒子が訪れた最良の位置 $p_i$ を格納
  * `q::P`: 中間結果の一時的ストレージとして機能する多様体 $\mathcal M$ 上の点；アロケーションを回避
  * `social_vec`:       `social_weight` に関連する接ベクトルの一時的ストレージ
  * `swarm`:            多様体上の点の集合（型 `AbstractVector{P}`） $\{a_i\}_{i=1}^{N}$

# コンストラクタ

```
ParticleSwarmState(M, initial_swarm, velocity; kawrgs...)
```

初期集団 `initial_swarm` と `velocities` で始まる多様体 `M` のための粒子群ソルバ状態を構築します。以下のデフォルトで使用される `p` は、群れの1つの点の型です。

# キーワード引数

  * `cognitive_weight=1.4`
  * `inertia=0.65`
  * `inverse_retraction_method=`[`default_inverse_retraction_method`](@extref `ManifoldsBase.default_inverse_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する逆再引き戻し $\operatorname{retr}^{-1}$、詳細は[再引き戻しとその逆に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再引き戻し $\operatorname{retr}$、詳細は[再引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `social_weight=1.4`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(500)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-4)`: 停止基準が満たされたことを示すファンクタ
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、詳細は[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照

# 参照

[`particle_swarm`](@ref)
