solve*poisson!( efield, particle*group, kernel*smoother, maxwell*solver, rho )

ρを蓄積し、ポアソン方程式を解く

  * `particle_group` : 粒子
  * `maxwell_solver` : マクスウェルソルバー (FEM 1D)
  * `kernel_smoother_0` : 粒子-メッシュ法
  * `rho` : 電荷密度のための事前割り当て配列
  * `efield_dofs` : 電場のスプライン係数 (1D)
