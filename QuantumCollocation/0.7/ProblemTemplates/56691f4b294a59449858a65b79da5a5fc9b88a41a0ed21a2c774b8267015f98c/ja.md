```
UnitaryVariationalProblem(
    system::VariationalQuantumSystem,
    goal::AbstractPiccoloOperator,
    T::Int,
    Δt::Union{Float64, <:AbstractVector{Float64}};
    robust_times::AbstractVector{<:Union{AbstractVector{Int}, Nothing}}=[nothing for s ∈ system.G_vars],
    sensitive_times::AbstractVector{<:Union{AbstractVector{Int}, Nothing}}=[nothing for s ∈ system.G_vars],
    kwargs...
)
```

量子制御軌道の最適化のためのユニタリ変分問題を構築します。

# 引数

  * `system::VariationalQuantumSystem`: 変分パラメータを含む制御される量子システム。
  * `goal::AbstractPiccoloOperator`: 軌道の終わりに達成すべきターゲットオペレーターまたは状態。
  * `T::Int`: 軌道内のタイムステップの総数。
  * `Δt::Union{Float64, <:AbstractVector{Float64}}`: タイムステップの期間またはタイムステップの期間のベクトル。
  * `robust_times::AbstractVector`: 軌道の変動に対するロバスト性が強制される時間。
  * `sensitive_times::AbstractVector`: 軌道の変動に対する感度が強化される時間。
  * `unitary_integrator`: ユニタリ進化に使用される積分器（デフォルト: `VariationalUnitaryIntegrator`）。
  * `state_name::Symbol`: 軌道内の状態変数の名前（デフォルト: `:Ũ⃗`）。
  * `variational_state_name::Symbol`: 変分状態変数の名前（デフォルト: `:Ũ⃗ₐ`）。
  * `variational_scales::AbstractVector`: 変分状態変数のスケーリングファクター（デフォルト: `1.0`）。
  * `control_name::Symbol`: 制御変数の名前（デフォルト: `:a`）。
  * `timestep_name::Symbol`: タイムステップ変数の名前（デフォルト: `:Δt`）。
  * `init_trajectory::Union{NamedTrajectory, Nothing}`: 最適化を開始するためのオプションの初期軌道。
  * `a_bound::Float64`: 制御変数 `a` の境界（デフォルト: `1.0`）。
  * `a_bounds::Vector`: 各制御変数の境界（デフォルト: `a_bound` で埋められたもの）。
  * `da_bound::Float64`: 制御変数の導関数の境界（デフォルト: `Inf`）。
  * `da_bounds::Vector`: 各制御変数の導関数の境界。
  * `dda_bound::Float64`: 制御変数の二次導関数の境界（デフォルト: `1.0`）。
  * `dda_bounds::Vector`: 各制御変数の二次導関数の境界。
  * `Δt_min::Float64`: 許可される最小タイムステップ期間。
  * `Δt_max::Float64`: 許可される最大タイムステップ期間。
  * `Q::Float64`: ユニタリ不忠実度目的の重み（デフォルト: `100.0`）。
  * `Q_v::Float64`: 感度目的の重み（デフォルト: `1.0`）。
  * `R`: 制御変数の正則化重み（デフォルト: `1e-2`）。
  * `R_a`, `R_da`, `R_dda`: 制御、導関数、および二次導関数の正則化重み。
  * `constraints::Vector`: 最適化問題の追加制約。
  * `piccolo_options::PiccoloOptions`: Piccolo最適化フレームワークの設定オプション。

# 戻り値

軌道、目的、積分器、および制約を含む最適化問題を表す `DirectTrajOptProblem` オブジェクト。

# 注意事項

この関数は、変分原理を使用して量子制御のための軌道最適化問題を構築します。ロバストで敏感な軌道設計、正則化、およびオプションの制約をサポートします。この問題は、Piccolo最適化フレームワークを使用して解決されます。
