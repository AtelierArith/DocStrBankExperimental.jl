```
open_rollout(
    ρ⃗₁::AbstractVector{<:Complex},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::OpenQuantumSystem;
    kwargs...
)
```

量子状態 `ρ⃗₁` を制御 `controls` の下で時間 `Δt` の間にロールアウトします。

# 引数

  * `ρ⃗₁::AbstractVector{<:Complex}`: 初期状態ベクトル
  * `controls::AbstractMatrix{<:Real}`: 制御行列
  * `Δt::AbstractVector`: 時間ステップ
  * `system::OpenQuantumSystem`: 量子システム

# キーワード引数

  * `show_progress::Bool=false`: 進行状況バーを表示
  * `integrator::Function=expv`: 積分関数
  * `exp_vector_product::Bool`: 積分器が指数ベクトル積であるかどうかを推測
