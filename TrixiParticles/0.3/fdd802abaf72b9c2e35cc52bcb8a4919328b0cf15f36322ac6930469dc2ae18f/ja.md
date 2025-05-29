```
RectangularShape(particle_spacing, n_particles_per_dimension, min_coordinates;
                 velocity=zeros(length(n_particles_per_dimension)),
                 mass=nothing, density=nothing, pressure=0.0,
                 acceleration=nothing, state_equation=nothing,
                 tlsph=false, loop_order=nothing)
```

粒子で満たされた長方形の形状。[`InitialCondition`](@ref)を返します。

# 引数

  * `particle_spacing`:           粒子間の間隔。
  * `n_particles_per_dimension`:  x、y、z（3Dのみ）方向の粒子数を含むタプル。
  * `min_coordinates`:            負の座標方向の隅の座標。

# キーワード

  * `velocity`:       各粒子の座標をその速度にマッピングする関数、または、定常流体速度の場合はこの速度を保持するベクトル。                   デフォルトでは速度はゼロです。
  * `mass`:           粒子密度と間隔から自動的に粒子質量を計算するための`nothing`（デフォルト）、または各粒子の座標をその質量にマッピングする関数、                   またはすべての粒子に対して一定の質量のスカラー。
  * `density`:        各粒子の座標をその密度にマッピングする関数、                   またはすべての粒子に対して一定の密度のスカラー。                   状態方程式を使用しない場合は必須。                   `state_equation`と一緒に使用することはできません。
  * `pressure`:       すべての粒子の圧力をこの値に設定するスカラー。                   これは[`EntropicallyDampedSPHSystem`](@ref)によってのみ使用され、                   システム内で初期圧力関数を使用する際に上書きされます。                   静水圧勾配と一緒に使用することはできません。
  * `acceleration`:   静水圧勾配で粒子を初期化するために、                   加速度ベクトルを渡すことができます。                   一つの座標方向の加速度のみがサポートされ、対角加速度はサポートされていません。                   これは粒子の圧力のみを変更します。                   [`WeaklyCompressibleSPHSystem`](@ref)を使用する場合は、                   対応する密度と質量で粒子を初期化するために`state_equation`も渡してください。                   [`EntropicallyDampedSPHSystem`](@ref)を使用する場合、                   システム内で初期圧力関数を使用する際に圧力が上書きされます。                   これは`pressure`キーワード引数と一緒に使用することはできません。
  * `state_equation`: `acceleration`を設定して静水圧勾配を計算する際に、                   `state_equation`が対応する密度を設定するために使用されます。                   `density`と一緒に使用することはできません。
  * `tlsph`:          [`TotalLagrangianSPHSystem`](@ref)では、粒子は形状の境界に配置する必要があり、                   流体のように1粒子半径離れた位置には配置できません。                   `tlsph=true`の場合、粒子は形状の境界に配置されます。
  * `coordinates_perturbation`: 粒子の位置に小さなランダムな変位を追加し、                             振幅は`coordinates_perturbation * particle_spacing`です。

# 例

```jldoctest; output = false, setup = :(particle_spacing = 0.1)
# 2D
rectangular = RectangularShape(particle_spacing, (5, 4), (1.0, 2.0), density=1000.0)

# 2Dの静水圧勾配。
# `state_equation`はWCSPHシステムと同じでなければなりません。
state_equation = StateEquationCole(sound_speed=20.0, exponent=7, reference_density=1000.0)
rectangular = RectangularShape(particle_spacing, (5, 4), (1.0, 2.0),
                               acceleration=(0.0, -9.81), state_equation=state_equation)

# 3D
rectangular = RectangularShape(particle_spacing, (5, 4, 7), (1.0, 2.0, 3.0), density=1000.0)

# 出力
┌──────────────────────────────────────────────────────────────────────────────────────────────────┐
│ InitialCondition{Float64}                                                                        │
│ ═════════════════════════                                                                        │
│ #dimensions: ……………………………………………… 3                                                                │
│ #particles: ………………………………………………… 140                                                              │
│ particle spacing: ………………………………… 0.1                                                              │
└──────────────────────────────────────────────────────────────────────────────────────────────────┘
```
