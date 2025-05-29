```
add_sphere!(Phase, Temp, Grid::AbstractGeneralGrid; cen::Tuple = (0,0,-1), radius::Number,
        phase = ConstantPhase(1).
        T=nothing, cell=false )
```

3Dモデルセットアップにフェーズと温度構造を持つ球体を追加します。これは、地球力学モデルにおけるモデル幾何学の作成を簡素化します。

# パラメータ

  * `Phase` - フェーズ配列（Gridと一貫性がある）
  * `Temp`  - 温度配列（Gridと一貫性がある）
  * `Grid` - LaMEMグリッド構造（通常はread*LaMEM*inputfileで取得）
  * `cen` - 球体の中心座標
  * `radius` - 球体の半径
  * `phase` - ボックスのフェーズを指定します。`ConstantPhase()`,`LithosphericPhases()`を参照
  * `T` - ボックスの温度を指定します。`ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`を参照
  * `cell` - trueの場合、`Phase`と`Temp`はセルの中心で定義されます

# 例

定数フェーズと温度の球体：

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
julia> add_sphere!(Phases,Temp,Grid, cen=(0,0,-1), radius=0.5, phase=ConstantPhase(2), T=ConstantTemp(800))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Cartesianモデルを作成
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # モデルをparaviewに保存
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
