```
RectangularTank(particle_spacing, fluid_size, tank_size, fluid_density;
                velocity=zeros(length(fluid_size)), fluid_mass=nothing,
                pressure=0.0,
                acceleration=nothing, state_equation=nothing,
                boundary_density=fluid_density,
                n_layers=1, spacing_ratio=1.0,
                min_coordinates=zeros(length(fluid_size)),
                faces=Tuple(trues(2 * length(fluid_size))))
```

流体で満たされた直方体タンクを使用して、ダムブレークスタイルのシミュレーションを設定します。

# 引数

  * `particle_spacing`:   流体粒子間の間隔。
  * `fluid_size`:         流体の寸法を `(x, y)`（または3Dの場合は `(x, y, z)`）で指定します。
  * `tank_size`:          タンクの寸法を `(x, y)`（または3Dの場合は `(x, y, z)`）で指定します。
  * `fluid_density`:      流体の静止密度。状態方程式を使用する際の `boundary_density` のデフォルトとしてのみ使用されます。

# キーワード

  * `velocity`:       各粒子の座標をその速度にマッピングする関数、または一定の流体速度の場合はこの速度を保持するベクトル。                   デフォルトでは速度はゼロです。
  * `fluid_mass`:     自動的に粒子密度と間隔から粒子質量を計算するための `nothing`（デフォルト）、または各粒子の座標をその質量にマッピングする関数、                   またはすべての粒子に対して一定の質量を指定するスカラー。
  * `pressure`:       すべての粒子の圧力をこの値に設定するスカラー。                   これは [`EntropicallyDampedSPHSystem`](@ref) にのみ使用され、                   システム内で初期圧力関数を使用する際に上書きされます。                   静水圧勾配と一緒に使用することはできません。
  * `acceleration`:   静水圧勾配で粒子を初期化するために、加速度ベクトルを渡すことができます。                   ただし、1つの座標方向の加速度のみがサポートされ、対角加速度はサポートされていません。                   これは粒子の圧力のみを変更します。                   [`WeaklyCompressibleSPHSystem`](@ref) を使用する場合は、                   対応する密度と質量で粒子を初期化するために `state_equation` も渡してください。                   [`EntropicallyDampedSPHSystem`](@ref) を使用する場合、                   システム内で初期圧力関数を使用する際に圧力が上書きされます。                   これは `pressure` キーワード引数と一緒に使用することはできません。
  * `state_equation`: `acceleration` を設定して静水圧勾配を計算する際に、                   `state_equation` は対応する密度を設定するために使用されます。                   `density` と一緒に使用することはできません。
  * `boundary_density`:   各境界粒子の密度（デフォルトでは流体密度に設定されています）
  * `n_layers`:           境界層の数。
  * `spacing_ratio`:      `particle_spacing` と境界粒子間隔の比率。                       値が2の場合、境界粒子間隔は流体粒子間隔の半分になります。
  * `min_coordinates`:    負の座標方向の隅の座標。
  * `faces`:              デフォルトではすべての面が生成されます。                       法線方向に面を生成するために、長さ4（2D）または6（3D）のビット配列を渡して面を設定します： -x,+x,-y,+y,-z,+z。

# フィールド

  * `fluid::InitialCondition`:    [`InitialCondition`](@ref) の流体用。
  * `boundary::InitialCondition`: [`InitialCondition`](@ref) の境界用。
  * `fluid_size::Tuple`:          丸めた後の各次元における流体のサイズを含むタプル。
  * `tank_size::Tuple`:           丸めた後の各次元におけるタンクのサイズを含むタプル。

# 例

```jldoctest; output = false, filter = r"RectangularTank.*", setup = :(particle_spacing = 0.1; water_width = water_depth = container_width = container_height = container_depth = 1.0; water_height = 0.5; fluid_density = 1000.0)
# 2D
setup = RectangularTank(particle_spacing, (water_width, water_height),
                        (container_width, container_height), fluid_density,
                        n_layers=2, spacing_ratio=3)

# 2D 静水圧勾配あり。
# `state_equation` は WCSPH システムと同じでなければなりません。
state_equation = StateEquationCole(sound_speed=10.0, exponent=1, reference_density=1000.0)
setup = RectangularTank(particle_spacing, (water_width, water_height),
                        (container_width, container_height), fluid_density,
                        acceleration=(0.0, -9.81), state_equation=state_equation)

# 3D
setup = RectangularTank(particle_spacing, (water_width, water_height, water_depth),
                        (container_width, container_height, container_depth), fluid_density,
                        n_layers=2)

# 出力
RectangularTank{3, 6, Float64}(...) *この行の残りはフィルターによって無視されます*
```

参照してください: [`reset_wall!`](@ref)。
