```
QuantumStateSmoothPulseProblem(system, ψ_inits, ψ_goals, T, Δt; kwargs...)
QuantumStateSmoothPulseProblem(system, ψ_init, ψ_goal, T, Δt; kwargs...)
QuantumStateSmoothPulseProblem(H_drift, H_drives, args...; kwargs...)
```

量子状態スムースパルス問題を作成します。目標は、制御パルス `a(t)` を見つけることで、すべての初期状態 `ψ_inits` を対応するターゲット状態 `ψ_goals` に `T` タイムステップのサイズ `Δt` を使用して駆動することです。この問題は、制御パルスの1階および2階導関数 `da(t)` と `dda(t)` も制御し、滑らかさを確保します。

# 引数

  * `system::AbstractQuantumSystem`: 量子システム。

または

  * `H_drift::AbstractMatrix{<:Number}`: ドリフトハミルトニアン。
  * `H_drives::Vector{<:AbstractMatrix{<:Number}}`: 制御ハミルトニアン。

とともに

  * `ψ_inits::Vector{<:AbstractVector{<:ComplexF64}}`: 初期状態。
  * `ψ_goals::Vector{<:AbstractVector{<:ComplexF64}}`: ターゲット状態。

または

  * `ψ_init::AbstractVector{<:ComplexF64}`: 初期状態。
  * `ψ_goal::AbstractVector{<:ComplexF64}`: ターゲット状態。

とともに

  * `T::Int`: タイムステップの数。
  * `Δt::Float64`: タイムステップのサイズ。

# キーワード引数

  * `state_name::Symbol=:ψ̃`: 状態変数の名前。
  * `control_name::Symbol=:a`: 制御変数の名前。
  * `timestep_name::Symbol=:Δt`: タイムステップ変数の名前。
  * `init_trajectory::Union{NamedTrajectory, Nothing}=nothing`: 初期軌道。
  * `a_bound::Float64=1.0`: 制御パルスの制約。
  * `a_bounds::Vector{Float64}=fill(a_bound, length(system.G_drives))`: 制御パルスの制約。
  * `a_guess::Union{Matrix{Float64}, Nothing}=nothing`: 制御パルスの初期推測。
  * `da_bound::Float64=Inf`: 制御パルスの1階導関数の制約。
  * `da_bounds::Vector{Float64}=fill(da_bound, length(system.G_drives))`: 制御パルスの1階導関数の制約。
  * `dda_bound::Float64=1.0`: 制御パルスの2階導関数の制約。
  * `dda_bounds::Vector{Float64}=fill(dda_bound, length(system.G_drives))`: 制御パルスの2階導関数の制約。
  * `Δt_min::Float64=0.5 * Δt`: 最小タイムステップサイズ。
  * `Δt_max::Float64=1.5 * Δt`: 最大タイムステップサイズ。
  * `drive_derivative_σ::Float64=0.01`: 駆動導関数のランダム初期化の標準偏差。
  * `Q::Float64=100.0`: 状態目的の重み。
  * `R=1e-2`: 制御パルスとその導関数の重み。
  * `R_a::Union{Float64, Vector{Float64}}=R`: 制御パルスの重み。
  * `R_da::Union{Float64, Vector{Float64}}=R`: 制御パルスの1階導関数の重み。
  * `R_dda::Union{Float64, Vector{Float64}}=R`: 制御パルスの2階導関数の重み。
  * `constraints::Vector{<:AbstractConstraint}=AbstractConstraint[]`: 制約。
  * `piccolo_options::PiccoloOptions=PiccoloOptions()`: Piccoloオプション。

```
