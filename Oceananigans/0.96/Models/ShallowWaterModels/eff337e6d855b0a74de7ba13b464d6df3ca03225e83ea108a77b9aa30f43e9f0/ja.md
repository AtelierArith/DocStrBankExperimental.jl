```
ShallowWaterModel(; grid,
                    gravitational_acceleration,
                          clock = Clock{eltype(grid)}(time = 0),
             momentum_advection = UpwindBiased(order=5),
               tracer_advection = WENO(),
                 mass_advection = WENO(),
                       coriolis = nothing,
            forcing::NamedTuple = NamedTuple(),
                        closure = nothing,
                     bathymetry = nothing,
                        tracers = (),
             diffusivity_fields = nothing,
boundary_conditions::NamedTuple = NamedTuple(),
            timestepper::Symbol = :RungeKutta3,
                    formulation = ConservativeFormulation())
```

`grid`上に`gravitational_acceleration`定数を持つ浅水モデルを構築します。

# キーワード引数

  * `grid`: (必須) `model`が解かれる解像度と離散幾何学。モデルが解かれるアーキテクチャ（CPU/GPU）は、グリッドのアーキテクチャから推測されます。
  * `gravitational_acceleration`: (必須) 重力加速度定数。
  * `clock`: モデルの`clock`。
  * `momentum_advection`: 速度を輸送するスキーム。`Oceananigans.Advection`を参照してください。デフォルト: `UpwindBiased(order=5)`。
  * `tracer_advection`: トレーサーを輸送するスキーム。`Oceananigans.Advection`を参照してください。デフォルト: `WENO()`。
  * `mass_advection`: 質量方程式を輸送するスキーム。`Oceananigans.Advection`を参照してください。デフォルト: `WENO()`。
  * `coriolis`: モデルの背景回転率のパラメータ。
  * `forcing`: 解の傾向に寄与するユーザー定義の強制関数の`NamedTuple`。
  * `closure`: `model`の乱流閉じ込め。`Oceananigans.TurbulenceClosures`を参照してください。
  * `bathymetry`: 底のバチメトリ。
  * `tracers`: モデル化されたトレーサーの名前を定義するシンボルのタプル、または事前に割り当てられた`CenterField`の`NamedTuple`。
  * `diffusivity_fields`: 閉じ込めが各タイムステップで拡散率を計算する必要がある場合に拡散率フィールドを格納します。
  * `boundary_conditions`: フィールド境界条件を含む`NamedTuple`。
  * `timestepper`: 時間ステッピング法を指定するシンボル。`:QuasiAdamsBashforth2`または`:RungeKutta3`（デフォルト）。
  * `formulation`: 動力学が保守的形式（`ConservativeFormulation()`; デフォルト）で表現されるか、非線形項のベクトル不変形式で非保守的形式（`VectorInvariantFormulation()`）で表現されるか。

!!! warning "形式-グリッド互換性要件"
    `ConservativeFormulation()`は`RectilinearGrid`を必要とします。`LatitudeLongitudeGrid`では`VectorInvariantFormulation()`を使用してください。

