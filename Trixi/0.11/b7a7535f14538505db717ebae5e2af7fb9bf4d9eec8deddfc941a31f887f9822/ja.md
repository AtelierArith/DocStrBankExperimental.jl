```
ParametersEulerGravity(; background_density=0.0,
                         gravitational_constant=1.0,
                         cfl=1.0,
                         resid_tol=1.0e-4,
                         n_iterations_max=10^4,
                         timestep_gravity=timestep_gravity_erk52_3Sstar!)
```

重力部分の[`SemidiscretizationEulerGravity`](@ref)のパラメータを設定します。

# 引数

  * `background_density<:Real`: (オイラー)密度から引かれる定数背景/基準密度ρ₀で、重力ソルバーのRHSソース項計算に使用されます。
  * `gravitational_constant<:Real`: 密度と速度場と一貫した単位である必要がある重力定数Gです。
  * `cfl<:Real`: ハイパーボリック拡散方程式を定常状態に進めるために使用される擬似時間ステッピングのCFL数です。
  * `resid_tol<:Real`: (おおよそ)定常状態に解かれるハイパーボリック拡散方程式の残差に対する絶対許容誤差です。
  * `n_iterations_max::Int`: 擬似時間重力ソルバーの最大反復回数です。`n_iterations <= 0`の場合、ソルバーは残差が`resid_tol`以下になるまで反復します。これにより、ソルバーが収束しない場合に無限ループが発生する可能性があります！
  * `timestep_gravity`: 重力ソルバーを1つの擬似時間ステップ進めるための関数です。最適化された3つのメソッドが利用可能です：                      1) `timestep_gravity_erk51_3Sstar!` (1次)、                     2) `timestep_gravity_erk52_3Sstar!` (2次)、                     3) `timestep_gravity_erk53_3Sstar!` (3次)。                     さらに、`timestep_gravity_carpenter_kennedy_erk54_2N!` (4次)も使用できます。
