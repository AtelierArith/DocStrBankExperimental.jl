```
VSMSolution
```

[solve!](@ref) 関数の解を格納するための構造体。`KiteModels.jl` に必要なすべての情報を含む必要があります。

# 属性

  * `panel_width_array`::Vector{Float64}: パネルの幅 [m]
  * `alpha_array`::Vector{Float64}: 各パネルの迎角 [rad]
  * cl_array::Vector{Float64}: パネルの揚力係数 [-]
  * cd_array::Vector{Float64}: パネルの抗力係数 [-]
  * cm_array::Vector{Float64}: パネルのピッチングモーメント係数 [-]
  * panel_lift::Vector{Float64}: パネルの揚力 [N]
  * panel_drag::Vector{Float64}: パネルの抗力 [N]
  * panel_moment::Vector{Float64}: パネルのスパン方向ベクトル周りのピッチングモーメント [Nm]
  * `f_body_3D`::Matrix{Float64}: 空力力の行列 (x, y, z ベクトル) [N]
  * `m_body_3D`::Matrix{Float64}: 空力モーメントの行列 [Nm]
  * `gamma_distribution`::Union{Nothing, Vector{Float64}}: パネルの循環を含むベクトル。
  * force::MVec3: KB 参照フレームにおける空力力ベクトル [N]
  * moment::MVec3: 参照点周りの空力モーメント [Mx, My, Mz] [Nm]
  * force_coeffs::MVec3: 空力力係数 [CFx, CFy, CFz] [-]
  * `moment_coeffs`::MVec3: 空力モーメント係数 [CMx, CMy, CMz] [-]
  * `moment_dist`::Vector{Float64}: 各パネルのスパン方向ベクトル周りのピッチングモーメント。 [Nm]
  * `moment_coeff_dist`::Vector{Float64}: 各パネルのスパン方向ベクトル周りのピッチングモーメント係数。 [-]
  * `solver_status`::SolverStatus: 列挙型、[SolverStatus](@ref) を参照してください。
