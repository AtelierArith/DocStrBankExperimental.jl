```
add_layer!(Phase, Temp, Grid::AbstractGeneralGrid; xlim::Tuple = (1,100), [ylim::Tuple = (0,20)], zlim::Tuple = (0,-100),
        phase = ConstantPhase(1),
        T=nothing, cell=false )
```

3Dモデルセットアップに相と温度構造を持つ層を追加します。最も一般的な使用法は、モデルセットアップに岩石圏の層を追加することです。これは、地球力学モデルにおけるモデルジオメトリの作成を簡素化します。

# パラメータ

  * `Phase` - 相配列（Gridと一致）
  * `Temp`  - 温度配列（Gridと一致）
  * `Grid` - グリッド構造（通常はread*LaMEM*inputfileで取得されますが、他のグリッドタイプでも可能）
  * `xlim` - ボックスの左/右座標
  * `ylim` - ボックスの前/後座標
  * `zlim` - ボックスの下/上座標
  * `phase` - ボックスの相を指定します。`ConstantPhase()`,`LithosphericPhases()`を参照
  * `T` - ボックスの温度を指定します。`ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`を参照

# 例

例 1) 定数相と温度の層

```julia-repl
julia> Grid = read_LaMEM_inputfile("test_files/SaltModels.dat")
LaMEM Grid:
  nel         : (32, 32, 32)
  marker/cell : (3, 3, 3)
  markers     : (96, 96, 96)
  x           ϵ [-3.0 : 3.0]
  y           ϵ [-2.0 : 2.0]
  z           ϵ [-2.0 : 0.0]
julia> Phases = zeros(Int32,   size(Grid.X));
julia> Temp   = zeros(Float64, size(Grid.X));
julia> add_layer!(Phases,Temp,Grid, zlim=(-50,0), phase=ConstantPhase(3), T=ConstantTemp(1000))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Cartesianモデルを作成
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # モデルをparaviewに保存
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```

例 2) 半空間冷却プロファイルのボックス

```julia-repl
julia> Grid = read_LaMEM_inputfile("test_files/SaltModels.dat")
julia> Phases = zeros(Int32,   size(Grid.X));
julia> Temp   = zeros(Float64, size(Grid.X));
julia> add_layer!(Phases,Temp,Grid, zlim=(-50,0), phase=ConstantPhase(3), T=HalfspaceCoolingTemp())
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Cartesianモデルを作成
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # モデルをparaviewに保存
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
