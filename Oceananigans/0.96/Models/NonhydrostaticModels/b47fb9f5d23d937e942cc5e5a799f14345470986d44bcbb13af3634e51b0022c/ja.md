```
非静水モデル(;           grid,
                                clock = Clock{eltype(grid)}(time = 0),
                            advection = Centered(),
                             buoyancy = nothing,
                             coriolis = nothing,
                         stokes_drift = nothing,
                  forcing::NamedTuple = NamedTuple(),
                              closure = nothing,
      boundary_conditions::NamedTuple = NamedTuple(),
                              tracers = (),
                          timestepper = :RungeKutta3,
        background_fields::NamedTuple = NamedTuple(),
        particles::ParticlesOrNothing = nothing,
biogeochemistry::AbstractBGCOrNothing = nothing,
                           velocities = nothing,
              nonhydrostatic_pressure = CenterField(grid),
         hydrostatic_pressure_anomaly = DefaultHydrostaticPressureAnomaly(),
                   diffusivity_fields = nothing,
                      pressure_solver = nothing,
                     auxiliary_fields = NamedTuple())
```

`grid`上で非静水の非圧縮流体モデルを構築し、`buoyancy != nothing`の場合はバウシネスク近似を使用します。デフォルトでは、すべての境界方向は剛体で侵入不可能です。

# キーワード引数

  * `grid`: (必須) `model`が解かれる解像度と離散幾何学。`model`が解かれるアーキテクチャ（CPU/GPU）は、`grid`のアーキテクチャから推測されます。グリッドは水平方向の次元$x$と$y$で定期的に間隔を空ける必要があることに注意してください。
  * `advection`: 速度とトレーサーを輸送するスキーム。`Oceananigans.Advection`を参照してください。
  * `buoyancy`: 浮力モデル。`Oceananigans.BuoyancyFormulations`を参照してください。
  * `coriolis`: モデルの背景回転率のパラメータ。
  * `stokes_drift`: 表面波に関連するストークス漂流場のパラメータ。デフォルト: `nothing`。
  * `forcing`: 解の傾向に寄与するユーザー定義の強制関数の`NamedTuple`。
  * `closure`: `model`の乱流閉じ込め。`Oceananigans.TurbulenceClosures`を参照してください。
  * `boundary_conditions`: フィールド境界条件を含む`NamedTuple`。
  * `tracers`: モデル化されたトレーサーの名前を定義するシンボルのタプル、または事前に割り当てられた`CenterField`の`NamedTuple`。
  * `timestepper`: 時間ステッピング法を指定するシンボル。`:QuasiAdamsBashforth2`または`:RungeKutta3`（デフォルト）。
  * `background_fields`: 背景フィールド（例：背景流）を持つ`NamedTuple`。デフォルト: `nothing`。
  * `particles`: 流れと共に輸送されるラグランジアン粒子。デフォルト: `nothing`。
  * `biogeochemistry`: `tracers`のための生物地球化学モデル。
  * `velocities`: モデルの速度。デフォルト: `nothing`。
  * `nonhydrostatic_pressure`: 非静水圧場。デフォルト: `CenterField(grid)`。
  * `hydrostatic_pressure_anomaly`: 浮力場と静水バランスにある非静水圧の一部を格納するオプションのフィールド。`CenterField(grid)`（デフォルト）の場合、異常は浮力場を垂直に積分することによって事前に計算されます。この場合、`nonhydrostatic_pressure`は静水異常から逸脱する圧力の部分のみを表します。`nothing`の場合、異常は計算されません。
  * `diffusivity_fields`: 拡散率フィールド。デフォルト: `nothing`。
  * `pressure_solver`: モデルで使用される圧力ソルバー。`nothing`（デフォルト）の場合、モデルコンストラクタは提供された`grid`に基づいてデフォルトを選択します。
  * `auxiliary_fields`: 補助フィールドの`NamedTuple`。デフォルト: `nothing`。
