```
add_cylinder!(Phase, Temp, Grid::AbstractGeneralGrid; base::Tuple = (-1,-1,-1.5), cap::Tuple = (-1,-1,-0.5), radius::Number,
        phase = ConstantPhase(1),
        T=nothing, cell=false )
```

3Dモデルセットアップにフェーズと温度構造を持つ円柱を追加します。これは、地球力学モデルにおけるモデルジオメトリの作成を簡素化します。

# パラメータ

  * `Phase` - フェーズ配列（Gridと一致）
  * `Temp`  - 温度配列（Gridと一致）
  * `Grid` - グリッド構造（通常は`read_LaMEM_inputfile`で取得）
  * `base` - 円柱の底の中心座標
  * `cap` - 円柱の頂の中心座標
  * `radius` - 円柱の半径
  * `phase` - ボックスのフェーズを指定します。`ConstantPhase()`,`LithosphericPhases()`を参照
  * `T` - ボックスの温度を指定します。`ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`を参照
  * `cell` - trueの場合、`Phase`と`Temp`はセルの中心で定義されます

# 例

定数フェーズと温度の円柱：

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
julia> add_cylinder!(Phases,Temp,Grid, base=(-1,-1,-1.5), cap=(1,1,-0.5), radius=0.25, phase=ConstantPhase(4), T=ConstantTemp(400))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # カルテジアンモデルを作成
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # モデルをパラビューに保存
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
