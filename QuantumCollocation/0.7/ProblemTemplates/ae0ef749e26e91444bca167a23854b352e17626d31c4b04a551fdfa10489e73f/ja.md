```
UnitarySamplingProblem(systemns, operator, T, Δt; kwargs...)
```

`UnitarySamplingProblem`は、量子制御問題であり、目標は一連の量子システムに対してターゲットユニタリ演算子を生成する制御パルスを見つけることです。制御はすべてのシステムで共有され、最適化は各システムの演算子を達成する制御パルスを見つけることを目指します。このアイデアは、問題の不確実性を反映する複数のシステムを含めることで堅牢な解を強制することです。

# 引数

  * `systems::AbstractVector{<:AbstractQuantumSystem}`: 量子システムのベクトル。
  * `operators::AbstractVector{<:AbstractPiccoloOperator}`: ターゲット演算子のベクトル。
  * `T::Int`: 時間ステップの数。
  * `Δt::Union{Float64, Vector{Float64}}`: 時間ステップの値または時間ステップのベクトル。

# キーワード引数

  * `system_labels::Vector{String} = string.(1:length(systems))`: 各システムのラベル。
  * `system_weights::Vector{Float64} = fill(1.0, length(systems))`: 各システムの重み。
  * `init_trajectory::Union{NamedTrajectory, Nothing} = nothing`: 初期軌道。
  * `state_name::Symbol = :Ũ⃗`: 状態変数の名前。
  * `control_name::Symbol = :a`: 制御変数の名前。
  * `timestep_name::Symbol = :Δt`: タイムステップ変数の名前。
  * `constraints::Vector{<:AbstractConstraint} = AbstractConstraint[]`: 制約。
  * `a_bound::Float64 = 1.0`: 制御振幅の境界。
  * `a_bounds::Vector{Float64} = fill(a_bound, length(systems[1].G_drives))`: 制御振幅の境界。
  * `a_guess::Union{Matrix{Float64}, Nothing} = nothing`: 制御振幅の初期推測。
  * `da_bound::Float64 = Inf`: 制御の一次導関数の境界。
  * `da_bounds::Vector{Float64} = fill(da_bound, length(systems[1].G_drives))`: 制御の一次導関数の境界。
  * `dda_bound::Float64 = 1.0`: 制御の二次導関数の境界。
  * `dda_bounds::Vector{Float64} = fill(dda_bound, length(systems[1].G_drives))`: 制御の二次導関数の境界。
  * `Δt_min::Float64 = 0.5 * Δt`: 最小時間ステップサイズ。
  * `Δt_max::Float64 = 1.5 * Δt`: 最大時間ステップサイズ。
  * `Q::Float64 = 100.0`: フィデリティ重み。
  * `R::Float64 = 1e-2`: 正則化重み。
  * `R_a::Union{Float64, Vector{Float64}} = R`: 制御振幅の正則化重み。
  * `R_da::Union{Float64, Vector{Float64}} = R`: 制御の一次導関数の正則化重み。
  * `R_dda::Union{Float64, Vector{Float64}} = R`: 制御の二次導関数の正則化重み。
  * `piccolo_options::PiccoloOptions = PiccoloOptions()`: Piccoloオプション。
