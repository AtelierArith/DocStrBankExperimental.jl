```
add_box!(Phase, Temp, Grid::AbstractGeneralGrid; xlim::Tuple = (20,100), [ylim::Tuple = (1,10)], zlim::Tuple = (10,80),
        Origin=nothing, StrikeAngle=0, DipAngle=0,
        phase = ConstantPhase(1),
        T=nothing,
        segments=nothing,
        cell=false )
```

フェーズと温度構造を3Dモデルセットアップに追加します。これにより、地球力学モデルでのモデルジオメトリの作成が簡素化されます。

# パラメータ

  * `Phase` - フェーズ配列（Gridと一致）
  * `Temp`  - 温度配列（Gridと一致）
  * `Grid` - グリッド構造（`GMG`の任意のグリッドタイプを使用可能）
  * `xlim` - ボックスの左/右座標
  * `ylim` - ボックスの前/後座標 [オプション; 指定しない場合はボックス全体を使用]
  * `zlim` - ボックスの下/上座標
  * `Origin` - ボックスを回転させるために使用される原点。デフォルトは左前上隅
  * `StrikeAngle` - スラブのストライク角
  * `DipAngle` - スラブのディップ角
  * `phase` - ボックスのフェーズを指定します。`ConstantPhase()`,`LithosphericPhases()`を参照
  * `T` - ボックスの温度を指定します。`ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`,`LithosphericTemp()`を参照
  * `segments` - ボックス内の複数のリッジセグメントを定義するためのオプションのパラメータ
  * `cell` - trueの場合、`Phase`と`Temp`は中心で定義されます

# 例

例 1) 定数フェーズと温度、ディップ角10度のボックス:

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
julia> add_box!(Phases,Temp,Grid, xlim=(0,500), zlim=(-50,0), phase=ConstantPhase(3), DipAngle=10, T=ConstantTemp(1000))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # カルテジアンモデルを作成
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # モデルをパラビューに保存
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```

例 2) 半空間冷却プロファイルのボックス

```julia-repl
julia> Grid = CartData(xyz_grid(-1000:10:1000,0,-660:10:0))
julia> Phases = zeros(Int32,   size(Grid));
julia> Temp   = zeros(Float64, size(Grid));
julia> add_box!(Phases,Temp,Grid, xlim=(0,500), zlim=(-50,0), phase=ConstantPhase(3), DipAngle=10, T=HalfspaceCoolingTemp(Age=30))
julia> Grid = addfield(Grid, (;Phases,Temp));       # カルテジアンモデルに追加
julia> write_paraview(Grid,"LaMEM_ModelSetup")  # モデルをパラビューに保存
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```

例 3) リッジ熱構造のボックス `julia-repl julia> Grid = CartData(xyz*grid(-1000:10:1000, -1000:10:1000, -660:5:0)) julia> Phases = fill(2, size(Grid)); julia> Temp   = fill(1350.0, size(Grid)); julia> segments = [((-500.0, -1000.0), (-500.0, 0.0)),                     ((-250.0, 0.0), (-250.0, 200.0)),                     ((-750.0, 200.0), (-750.0, 1000.0))]; julia> lith = LithosphericPhases(Layers=[15 55], Phases=[1 2], Tlab=1250); julia> add*box!(Phases, Temp, Grid; xlim=(-1000.0, 0.0), ylim=(-500.0, 500.0),                  zlim=(-80.0, 0.0), phase=lith,                  T=SpreadingRateTemp(SpreadingVel=3), segments=segments) julia> Grid = addfield(Grid, (; Phases, Temp));       # カルテジアンモデルに追加 julia> write*paraview(Grid, "Ridge*Thermal*Structure")  # モデルをパラビューに保存 1-element Vector{String}:  "Ridge*Thermal_Structure.vts"`
