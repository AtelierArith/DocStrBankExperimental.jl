```
EntropicallyDampedSPHSystem(initial_condition, smoothing_kernel,
                            smoothing_length, sound_speed;
                            pressure_acceleration=inter_particle_averaged_pressure,
                            density_calculator=SummationDensity(),
                            transport_velocity=nothing,
                            alpha=0.5, viscosity=nothing,
                            acceleration=ntuple(_ -> 0.0, NDIMS), surface_tension=nothing,
                            surface_normal_method=nothing, buffer_size=nothing,
                            reference_particle_spacing=0.0, source_terms=nothing)
```

流体の粒子のためのシステム。[弱圧縮性SPHスキーム](@ref wcsph)が状態方程式を使用するのに対し、このスキームは圧力を計算するために圧力進化方程式を使用します。方法の詳細については、[エントロピー減衰人工圧縮性SPH](@ref edac)を参照してください。

# 引数

  * `initial_condition`:  システムの粒子を表す初期条件。
  * `sound_speed`:        音速。
  * `smoothing_kernel`:   このシステムで使用されるスムージングカーネル。                       [スムージングカーネル](@ref smoothing_kernel)を参照してください。
  * `smoothing_length`:   このシステムで使用されるスムージング長。                       [スムージングカーネル](@ref smoothing_kernel)を参照してください。

# キーワード引数

  * `viscosity`:                  このシステムの粘度モデル（デフォルト：粘度なし）。                               推奨：[`ViscosityAdami`](@ref)。
  * `acceleration`:               システムの加速度ベクトル。（デフォルト：ゼロベクトル）
  * `pressure_acceleration`:      圧力加速度の定式化（デフォルト：粒子間平均圧力）。                               `nothing`に設定すると、対応する[密度計算機](@ref density_calculator)のための圧力加速度の定式化が選択されます。
  * `density_calculator`:         [密度計算機](@ref density_calculator)（デフォルト：[`SummationDensity`](@ref)）
  * `transport_velocity`:         [輸送速度の定式化 (TVF)](@ref transport_velocity_formulation)。 デフォルトはTVFなし。
  * `buffer_size`:                バッファ粒子の数。                               [`OpenBoundarySPHSystem`](@ref)を使用してシミュレーションする際に必要です。
  * `correction`:                 このシステムで使用される補正方法。（デフォルト：補正なし、[補正](@ref corrections)を参照）
  * `source_terms`:               このシステムの追加のソース項。デフォルトでは`nothing`である必要がありますが、                               `(coords, velocity, density, pressure, t)`の関数である必要があります。                               （これらは単一粒子の量であり）、加速度に追加される`Tuple`または`SVector`を返します。                               例えば、[`SourceTermDamping`](@ref)を参照してください。                               これらのソース項は、[`BoundaryModelDummyParticles`](@ref)および[`AdamiPressureExtrapolation`](@ref)を使用して境界圧力を計算する際には使用されません。                               重力のようなソース項には、キーワード引数`acceleration`を代わりに使用する必要があります。
  * `surface_tension`:            このSPHシステムで使用される表面張力モデル。（デフォルト：表面張力なし）
  * `surface_normal_method`:      このSPHシステムで使用される表面法線法。                               （デフォルト：表面法線法なし、または表面張力モデルが使用されている場合は`ColorfieldSurfaceNormal()`）
  * `reference_particle_spacing`: 境界での値の重み付けに使用される参照粒子間隔。                               現在、表面張力を使用する場合にのみ必要です。
  * `color_value`:                システム内の粒子の色を初期化するために使用される値。
