```
UnitarySmoothPulseProblem(system::AbstractQuantumSystem, operator, T, Δt; kwargs...)
UnitarySmoothPulseProblem(H_drift, H_drives, operator, T, Δt; kwargs...)
```

滑らかな制御パルスによって強制される自由時間ユニタリゲート問題のための `DirectTrajOptProblem` を構築します。これは、パルス軌道の二次導関数を制約することによって実現されます。すなわち、

$$
\begin{aligned}
\underset{\vec{\tilde{U}}, a, \dot{a}, \ddot{a}, \Delta t}{\text{minimize}} & \quad
Q \cdot \ell\qty(\vec{\tilde{U}}_T, \vec{\tilde{U}}_{\text{goal}}) + \frac{1}{2} \sum_t \qty(R_a a_t^2 + R_{\dot{a}} \dot{a}_t^2 + R_{\ddot{a}} \ddot{a}_t^2) \\
\text{ subject to } & \quad \vb{P}^{(n)}\qty(\vec{\tilde{U}}_{t+1}, \vec{\tilde{U}}_t, a_t, \Delta t_t) = 0 \\
& \quad a_{t+1} - a_t - \dot{a}_t \Delta t_t = 0 \\
& \quad \dot{a}_{t+1} - \dot{a}_t - \ddot{a}_t \Delta t_t = 0 \\
& \quad |a_t| \leq a_{\text{bound}} \\
& \quad |\ddot{a}_t| \leq \ddot{a}_{\text{bound}} \\
& \quad \Delta t_{\text{min}} \leq \Delta t_t \leq \Delta t_{\text{max}} \\
\end{aligned}
$$

ここで、$U \in SU(N)$ の場合、

$$
\ell\qty(\vec{\tilde{U}}_T, \vec{\tilde{U}}_{\text{goal}}) =
\abs{1 - \frac{1}{N} \abs{ \tr \qty(U_{\text{goal}}, U_T)} }
$$

は *不忠実度* 目的関数であり、$Q$ は重み、$R_a$, $R_{\dot{a}}$, および $R_{\ddot{a}}$ は正則化項の重みであり、$\vb{P}^{(n)}$ は $n$ 次のパデ積分器です。

# 引数

  * `system::AbstractQuantumSystem`: 制御されるシステム

または

  * `H_drift::AbstractMatrix{<:Number}`: ドリフトハミルトニアン
  * `H_drives::Vector{<:AbstractMatrix{<:Number}}`: 制御ハミルトニアン

とともに

  * `goal::AbstractPiccoloOperator`: 目標ユニタリ、`EmbeddedOperator` または `Matrix{ComplexF64}` の形式
  * `T::Int`: タイムステップの数
  * `Δt::Float64`: （初期）タイムステップサイズ

# キーワード引数

  * `piccolo_options::PiccoloOptions=PiccoloOptions()`: Piccolo ソルバーのオプション
  * `state_name::Symbol = :Ũ⃗`: 状態の名前
  * `control_name::Symbol = :a`: 制御の名前
  * `timestep_name::Symbol = :Δt`: タイムステップの名前
  * `init_trajectory::Union{NamedTrajectory, Nothing}=nothing`: 使用する初期軌道
  * `a_guess::Union{Matrix{Float64}, Nothing}=nothing`: 制御パルスの初期推測
  * `a_bound::Float64=1.0`: 制御パルスの制約
  * `a_bounds::Vector{Float64}=fill(a_bound, length(system.G_drives))`: 各ドライブの制御パルスの制約
  * `da_bound::Float64=Inf`: 制御パルス導関数の制約
  * `da_bounds::Vector{Float64}=fill(da_bound, length(system.G_drives))`: 各ドライブの制御パルス導関数の制約
  * `dda_bound::Float64=1.0`: 制御パルス二次導関数の制約
  * `dda_bounds::Vector{Float64}=fill(dda_bound, length(system.G_drives))`: 各ドライブの制御パルス二次導関数の制約
  * `Δt_min::Float64=Δt isa Float64 ? 0.5 * Δt : 0.5 * mean(Δt)`: 最小タイムステップサイズ
  * `Δt_max::Float64=Δt isa Float64 ? 1.5 * Δt : 1.5 * mean(Δt)`: 最大タイムステップサイズ
  * `Q::Float64=100.0`: 不忠実度目的の重み
  * `R=1e-2`: 正則化項の重み
  * `R_a::Union{Float64, Vector{Float64}}=R`: 制御パルスの正則化項の重み
  * `R_da::Union{Float64, Vector{Float64}}=R`: 制御パルス導関数の正則化項の重み
  * `R_dda::Union{Float64, Vector{Float64}}=R`: 制御パルス二次導関数の正則化項の重み
  * `constraints::Vector{<:AbstractConstraint}=AbstractConstraint[]`: 強制する制約
