```
WeaklyCompressibleSPHSystem(initial_condition,
                            density_calculator, state_equation,
                            smoothing_kernel, smoothing_length;
                            viscosity=nothing, density_diffusion=nothing,
                            transport_velocity=nothing,
                            acceleration=ntuple(_ -> 0.0, NDIMS),
                            buffer_size=nothing,
                            correction=nothing, source_terms=nothing,
                            surface_tension=nothing, surface_normal_method=nothing,
                            reference_particle_spacing=0.0))
```

流体の粒子のためのシステム。弱圧縮性SPH（WCSPH）スキームが使用されており、堅い状態方程式が小さな密度変動に対して大きな圧力変化を生成します。手法の詳細については[Weakly Compressible SPH](@ref wcsph)を参照してください。

# 引数

  * `initial_condition`:  [`InitialCondition`](@ref)はシステムの粒子を表します。
  * `density_calculator`: システムのための密度計算機。                       [`ContinuityDensity`](@ref)および[`SummationDensity`](@ref)を参照してください。
  * `state_equation`:     システムの状態方程式。[`StateEquationCole`](@ref)を参照してください。
  * `smoothing_kernel`:   このシステムで使用されるスムージングカーネル。                       [Smoothing Kernels](@ref smoothing_kernel)を参照してください。
  * `smoothing_length`:   このシステムで使用されるスムージング長。                       [Smoothing Kernels](@ref smoothing_kernel)を参照してください。

# キーワード引数

  * `viscosity`:                  このシステムのための粘度モデル（デフォルト：粘度なし）。                               [`ArtificialViscosityMonaghan`](@ref)または[`ViscosityAdami`](@ref)を参照してください。
  * `transport_velocity`:         [Transport Velocity Formulation (TVF)](@ref transport_velocity_formulation)。デフォルトはTVFなし。
  * `density_diffusion`:          このシステムのための密度拡散項。[`DensityDiffusion`](@ref)を参照してください。
  * `acceleration`:               システムの加速度ベクトル。（デフォルト：ゼロベクトル）
  * `buffer_size`:                バッファ粒子の数。                               [`OpenBoundarySPHSystem`](@ref)を使用してシミュレーションする際に必要です。
  * `correction`:                 このシステムで使用される補正方法。（デフォルト：補正なし、[Corrections](@ref corrections)を参照）
  * `source_terms`:               このシステムのための追加のソース項。デフォルトでは`nothing`                               （デフォルト）、または`(coords, velocity, density, pressure, t)`の関数                               （これらは単一粒子の量）であり、加速度に加算される`Tuple`                               または`SVector`を返します。                               例えば、[`SourceTermDamping`](@ref)を参照してください。                               これらのソース項は、[`BoundaryModelDummyParticles`](@ref)および[`AdamiPressureExtrapolation`](@ref)を使用して境界圧力の計算には使用されません。                               重力のようなソース項には、キーワード引数`acceleration`を代わりに使用する必要があります。
  * `surface_tension`:            このSPHシステムで使用される表面張力モデル。（デフォルト：表面張力なし）
  * `surface_normal_method`:      このSPHシステムで使用される表面法線法。                               （デフォルト：表面法線法なし、または表面張力モデルが使用されている場合は`ColorfieldSurfaceNormal()`）
  * `reference_particle_spacing`: 境界での値の重み付けに使用される参照粒子間隔、                               現在は表面張力を使用する場合にのみ必要です。
  * `color_value`:                システム内の粒子の色を初期化するために使用される値。
