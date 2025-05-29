```
    add_polygon!(Phase, Temp, Grid::AbstractGeneralGrid; xlim=(), ylim::Tuple = (0.0,0.8), zlim=(), phase = ConstantPhase(1), T=nothing, cell=false )
```

フェーズと温度構造を持つポリゴンを3Dモデルセットアップに追加します。これは、地球力学モデルにおけるモデルジオメトリの作成を簡素化します。

# パラメータ

  * `Phase` - フェーズ配列（Gridと一致）
  * `Temp`  - 温度配列（Gridと一致）
  * `Grid`  - グリッド構造（通常はread*LaMEM*inputfileで取得）
  * `xlim`  - ポリゴン点の`x`座標、zlimと同じ順序、ポイント数は無制限
  * `ylim`  - `y`座標、長さの制限が可能（2つの値（開始と停止））
  * `zlim`  - ポリゴン点の`z`座標、xlimと同じ順序、ポイント数は無制限
  * `phase` - ボックスのフェーズを指定します。`ConstantPhase()`を参照
  * `T`     - ボックスの温度を指定します。`ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`を参照
  * `cell`  - trueの場合、`Phase`と`Temp`はセル中心で定義されます

# 例

定数フェーズと温度のポリゴン：

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
julia> add_polygon!(Phase, Temp, Cart; xlim=(0,0, 1.6, 2.0),ylim=(0,0.8), zlim=(0,-1,-2,0), phase = ConstantPhase(8), T=ConstantTemp(30))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Cartesianモデルを作成
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # モデルをparaviewに保存
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
