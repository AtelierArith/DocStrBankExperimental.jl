```
BoundaryModelDummyParticles(initial_density, hydrodynamic_mass,
                            density_calculator, smoothing_kernel,
                            smoothing_length; viscosity=nothing,
                            state_equation=nothing, correction=nothing,
                            reference_particle_spacing=0.0)
```

`BoundarySPHSystem`の境界モデル。

# 引数

  * `initial_density`: 各境界粒子の初期密度を保持するベクター。
  * `hydrodynamic_mass`: 各境界粒子の「流体力学的質量」を保持するベクター。                      詳細については上記の説明を参照してください。
  * `density_calculator`: 境界粒子の流体力学的密度を計算するための戦略。                       詳細については以下の説明を参照してください。
  * `smoothing_kernel`: スムージングカーネルは隣接する流体システムと同じである必要があります。
  * `smoothing_length`: スムージング長は隣接する流体システムと同じである必要があります。

# キーワード

  * `state_equation`:             これは隣接する流体システムと同じである必要があります                               (例えば[`StateEquationCole`](@ref)を参照)。
  * `correction`:                 隣接する流体システムの補正方法 ( [Corrections](@ref corrections)を参照)。
  * `viscosity`:                  スリップ（デフォルト）またはノンスリップ条件。詳細については以下を参照                               してください。
  * `reference_particle_spacing`: 境界での値の重み付けに使用される参照粒子間隔、                               現在は表面張力を使用する場合にのみ必要です。

# 例

```jldoctest; output = false, setup = :(densities = [1.0, 2.0, 3.0]; masses = [0.1, 0.2, 0.3]; smoothing_kernel = SchoenbergCubicSplineKernel{2}(); smoothing_length = 0.1)
# 自由スリップ条件
boundary_model = BoundaryModelDummyParticles(densities, masses, AdamiPressureExtrapolation(),
                                             smoothing_kernel, smoothing_length)

# ノンスリップ条件
boundary_model = BoundaryModelDummyParticles(densities, masses, AdamiPressureExtrapolation(),
                                             smoothing_kernel, smoothing_length,
                                             viscosity=ViscosityAdami(nu=1e-6))

# 出力
BoundaryModelDummyParticles(AdamiPressureExtrapolation, ViscosityAdami)
```
