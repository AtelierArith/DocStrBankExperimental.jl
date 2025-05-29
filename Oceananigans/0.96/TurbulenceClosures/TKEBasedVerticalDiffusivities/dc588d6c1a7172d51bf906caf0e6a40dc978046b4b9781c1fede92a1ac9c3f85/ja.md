```
CATKEVerticalDiffusivity([time_discretization = VerticallyImplicitTimeDiscretization(),
                         FT = Float64;]
                         mixing_length = CATKEMixingLength(),
                         turbulent_kinetic_energy_equation = CATKEEquation(),
                         maximum_tracer_diffusivity = Inf,
                         maximum_tke_diffusivity = Inf,
                         maximum_viscosity = Inf,
                         minimum_tke = 1e-9,
                         minimum_convective_buoyancy_flux = 1e-11,
                         negative_tke_damping_time_scale = 1minute,
                         tke_time_step = nothing)
```

小規模な海洋乱流に基づく垂直混合のための `CATKEVerticalDiffusivity` turbulence closure を返します。これは、サブグリッド乱流運動エネルギー（TKE）の予測進化に基づいています。

!!! note "CATKE 垂直拡散係数"
    `CATKEVerticalDiffusivity` は新しい乱流閉じ込め拡散係数です。その自由パラメータのデフォルト値は、大規模渦シミュレーションに対するキャリブレーションから得られています。詳細については、[Wagner25catke](@cite)を参照してください。

    使用には注意が必要で、物理に関する問題は https://github.com/CliMA/Oceananigans.jl/issues で報告してください。


# 引数

  * `time_discretization`: `ExplicitTimeDiscretization()` または `VerticallyImplicitTimeDiscretization()` のいずれか; デフォルトは `VerticallyImplicitTimeDiscretization()`。
  * `FT`: 浮動小数点型; デフォルトは `Float64`。

# キーワード引数

  * `mixing_length`: 混合長の定式化; デフォルト: `CATKEMixingLength()`。
  * `turbulent_kinetic_energy_equation`: TKE方程式; デフォルト: `CATKEEquation()`。
  * `maximum_tracer_diffusivity`: トレーサー拡散係数の最大値。`maximum_tracer_diffusivity` より大きい CATKE予測のトレーサー拡散係数はクリップされます。デフォルト: `Inf`。
  * `maximum_tke_diffusivity`: TKE拡散係数の最大値。`maximum_tke_diffusivity` より大きい CATKE予測のTKE拡散係数はクリップされます。デフォルト: `Inf`。
  * `maximum_viscosity`: 運動量拡散係数の最大値。`maximum_viscosity` より大きい CATKE予測の運動量拡散係数はクリップされます。デフォルト: `Inf`。
  * `minimum_tke`: 乱流運動エネルギーの最小値。例えば、内部波の崩壊による混合のための「背景」TKEレベルの存在をモデル化するために使用できます。デフォルト: 1e-9。
  * `minimum_convective_buoyancy_flux` 対流浮力フラックスの最小値。デフォルト: 1e-11。
  * `negative_tke_damping_time_scale`: TKEの疑似負の値に対する減衰時間スケール。通常、TKEの対流に関連する振動誤差によって生成されます。デフォルト: 1分。

# 参考文献

Wagner, G. L., Hillier, A., Constantinou, N. C., Silvestri, S., Souza, A., Burns, K., Hill, C., Campin, J.-M., Marshall, J., and Ferrari, R. (2025). "Formulation and calibration of CATKE, a one-equation parameterization for microscale ocean mixing." J. Adv. Model. Earth Sy., 17, e2024MS004522.
