```
variational_unitary_rollout(
    Ũ⃗_init::AbstractVector{<:Real},
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector{<:Real},
    system::VariationalQuantumSystem;
    show_progress::Bool=false,
    integrator::Function=expv,
    exp_vector_product::Bool=infer_is_evp(integrator)
)
variational_unitary_rollout(
    controls::AbstractMatrix{<:Real},
    Δt::AbstractVector,
    system::VariationalQuantumSystem;
    kwargs...
)
variational_unitary_rollout(
    traj::NamedTrajectory,
    system::VariationalQuantumSystem;
    unitary_name::Symbol=:Ũ⃗,
    drive_name::Symbol=:a,
    kwargs...
)
```

与えられた制御軌道の下で量子状態の変分進化をシミュレートします。

# 戻り値

  * `Ũ⃗::Matrix{<:Real}`: 各タイムステップでの進化したユニタリ。
  * `Ũ⃗_vars::Vector{<:Matrix{<:Real}}`: 変分パラメータに対するユニタリの変分導関数。

# 注意事項

この関数は、システムの変分生成器を使用してユニタリの変分進化を計算します。自動微分可能な制御とタイムステップをサポートしており、最適化タスクに適しています。変分導関数は状態の進化とともに計算され、感度分析や勾配ベースの最適化を可能にします。
