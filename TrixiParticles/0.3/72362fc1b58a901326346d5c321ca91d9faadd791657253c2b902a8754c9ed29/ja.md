```
trixi2vtk(vu_ode, semi, t; iter=nothing, output_directory="out", prefix="",
          write_meta_data=true, max_coordinates=Inf, custom_quantities...)
```

TrixiシミュレーションデータをVTK形式に変換します。

# 引数

  * `vu_ode`: TrixiParticles ODEシステムのある時刻における解。これは、例で返される`ArrayPartition`を期待します。`sol.u[end]`として。
  * `semi`: TrixiParticlesシミュレーションの半離散化。
  * `t`: シミュレーションの現在の時間。

# キーワード

  * `iter=nothing`:           複数の反復を別々のファイルに保存する場合の反復番号。この番号はファイル名に単に追加されます。
  * `output_directory="out"`: 出力ディレクトリのパス。
  * `prefix=""`:              出力ファイルのプレフィックス。
  * `write_meta_data=true`:   メタデータを書き込みます。
  * `max_coordinates=Inf`     粒子の座標は、その絶対値がこの閾値を超えるとクリップされます。
  * `custom_quantities...`:   VTK出力に含める追加のカスタム量。                           各カスタム量は`(system, data, t)`の関数でなければならず、                           これは各システムに対して呼び出されます。ここで`data`は、                           システムタイプに依存するフィールドを持つ名前付きタプルであり、                           `t`は現在のシミュレーション時間です。                           各システムの利用可能なデータは`available_data(system)`で確認できます。                           ここで使用できる事前定義されたカスタム量のリストについては、                           [Custom Quantities](@ref custom_quantities)を参照してください。

# 例

```jldoctest; output = false, setup = :(trixi_include(@__MODULE__, joinpath(examples_dir(), "fluid", "hydrostatic_water_column_2d.jl"), tspan=(0.0, 0.01), callbacks=nothing))
trixi2vtk(sol.u[end], semi, 0.0, iter=1, output_directory="output", prefix="solution")

# 各システムの運動エネルギーを「my_custom_quantity」として追加で保存
trixi2vtk(sol.u[end], semi, 0.0, iter=1, my_custom_quantity=kinetic_energy)

# 出力

```
