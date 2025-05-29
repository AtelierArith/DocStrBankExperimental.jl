```
ParticleSwarmState{P,T} <: AbstractManoptSolverState
```

粒子群最適化アルゴリズムを説明します。

# フィールド

  * `cognitive_weight`:          (`1.4`) 認知重み係数
  * `inertia`:                   (`0.65`) 粒子の慣性
  * `inverse_retraction_method`: (`default_inverse_retraction_method(M, eltype(swarm))`) 使用する逆引き戻し
  * `retraction_method`:         (`default_retraction_method(M, eltype(swarm))`) 使用する引き戻し
  * `social_weight`:             (`1.4`) 社会的重み係数
  * `stopping_criterion`:        (`[`StopAfterIteration`](@ref)`(500) | `[`StopWhenChangeLess`](@ref)`(1e-4)`) 停止条件を示す[`StoppingCriterion`](@ref)から継承されたファンクタ。
  * `vector_transport_method`:  (`default_vector_transport_method(M, eltype(swarm))`) 使用するベクトル輸送
  * `velocity`:                 粒子の速度を表す接ベクトルのセット（型 `AbstractVector{T}`）

# 内部および一時的フィールド

  * `cognitive_vector`: 認知重み係数に関連する接ベクトルの一時的ストレージ
  * `p`:                すべての粒子が訪れた最良点 $p$ のストレージ
  * `positional_best`:  各粒子が訪れた最良位置 $p_i$ を保存
  * `q`:                アルゴリズムのステップ中にアロケーションを避けるためのポイントの一時的ストレージ
  * `social_vec`:       社会的重み係数に関連する接ベクトルの一時的ストレージ
  * `swarm`:            多様体上の点のセット（型 `AbstractVector{P}`） $\{s_i\}_{i=1}^N$

# コンストラクタ

```
ParticleSwarmState(M, initial_swarm, velocity; kawrgs...)
```

初期集団 `x0` と `velocities` で始まる多様体 `M` のための粒子群ソルバーステートを構築します。多様体は前述のデフォルトで使用されます。デフォルトを持つすべてのフィールドはここでキーワード引数です。

# 参照

[`particle_swarm`](@ref)
