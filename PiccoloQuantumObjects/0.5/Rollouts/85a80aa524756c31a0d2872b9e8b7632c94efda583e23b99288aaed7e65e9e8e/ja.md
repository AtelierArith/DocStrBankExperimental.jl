```
unitary_rollout(
    Ũ⃗_init::AbstractVector{<:Real},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::AbstractQuantumSystem;
    kwargs...
)
```

制御 `controls` の下で時間 `Δt` の間に初期ユニタリベクトル `Ũ⃗_init` を同型ユニタリ演算子として展開します。

# 引数

  * `Ũ⃗_init::AbstractVector{<:Real}`: 初期ユニタリベクトル
  * `controls::AbstractMatrix{<:Real}`: 制御行列
  * `Δt::AbstractVector`: 時間ステップ
  * `system::AbstractQuantumSystem`: 量子システム

# キーワード引数

  * `show_progress::Bool=false`: 進行状況バーを表示
  * `integrator::Function=expv`: 積分関数
  * `exp_vector_product::Bool`: 積分器が指数ベクトル積であるかどうかを推測
