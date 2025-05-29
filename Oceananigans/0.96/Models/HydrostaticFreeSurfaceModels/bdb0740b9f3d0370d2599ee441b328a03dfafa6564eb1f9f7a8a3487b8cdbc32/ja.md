```
HydrostaticFreeSurfaceModel(; grid,
                            clock = Clock{Float64}(time = 0),
                            momentum_advection = VectorInvariant(),
                            tracer_advection = Centered(),
                            buoyancy = SeawaterBuoyancy(eltype(grid)),
                            coriolis = nothing,
                            free_surface = default_free_surface(grid, gravitational_acceleration=g_Earth),
                            forcing::NamedTuple = NamedTuple(),
                            closure = nothing,
                            timestepper = :QuasiAdamsBashforth2,
                            boundary_conditions::NamedTuple = NamedTuple(),
                            tracers = (:T, :S),
                            particles::ParticlesOrNothing = nothing,
                            biogeochemistry::AbstractBGCOrNothing = nothing,
                            velocities = nothing,
                            pressure = nothing,
                            diffusivity_fields = nothing,
                            auxiliary_fields = NamedTuple(),
                            vertical_coordinate = default_vertical_coordinate(grid))
```

`grid`上に自由表面を持つ静水モデルを構築します。

# キーワード引数

  * `grid`: (必須) `model`が解かれる解像度と離散幾何学。`model`が解かれるアーキテクチャ（CPU/GPU）は`grid`のアーキテクチャから推測されます。
  * `momentum_advection`: 速度を輸送するスキーム。`Oceananigans.Advection`を参照してください。
  * `tracer_advection`: トレーサーを輸送するスキーム。`Oceananigans.Advection`を参照してください。
  * `buoyancy`: 浮力モデル。`Oceananigans.BuoyancyFormulations`を参照してください。
  * `coriolis`: モデルの背景回転率のパラメータ。
  * `free_surface`: 自由表面モデル。デフォルトの自由表面ソルバーは`grid`の幾何学に依存します。`grid`が水平方向に定期的に間隔を空けた`RectilinearGrid`である場合、デフォルトは`solver_method = :FFTBasedPoissonSolver`を持つ`ImplicitFreeSurface`ソルバーです。それ以外の場合、デフォルトは`SplitExplicitFreeSurface`です。
  * `tracers`: モデル化されたトレーサーの名前を定義するシンボルのタプル、または事前に割り当てられた`CenterField`の`NamedTuple`。
  * `forcing`: 解の傾向に寄与するユーザー定義の強制関数の`NamedTuple`。
  * `closure`: `model`の乱流閉じ込め。`Oceananigans.TurbulenceClosures`を参照してください。
  * `timestepper`: 時間ステッピング法を指定するシンボル。`：QuasiAdamsBashforth2`（デフォルト）または`：SplitRungeKutta3`のいずれか。
  * `boundary_conditions`: フィールド境界条件を含む`NamedTuple`。
  * `particles`: 流れと共に輸送されるラグランジュ粒子。デフォルト: `nothing`。
  * `biogeochemistry`: `tracers`のための生物地球化学モデル。
  * `velocities`: モデルの速度。デフォルト: `nothing`。
  * `pressure`: 静水圧場。デフォルト: `nothing`。
  * `diffusivity_fields`: 拡散率フィールド。デフォルト: `nothing`。
  * `auxiliary_fields`: 補助フィールドの`NamedTuple`。デフォルト: `nothing`。
  * `vertical_coordinate`: グリッド進化のアルゴリズム: ZStar()またはZCoordinate()。デフォルト: MutableVerticalDiscretizationを持つグリッドの場合はZStar(); それ以外の場合はZCoordinate()。
