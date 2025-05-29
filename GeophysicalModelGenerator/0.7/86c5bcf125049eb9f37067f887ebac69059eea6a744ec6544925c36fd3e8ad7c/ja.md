```
add_ellipsoid!(Phase, Temp, Grid::AbstractGeneralGrid; cen::Tuple = (-1,-1,-1), axes::Tuple = (0.2,0.1,0.5),
        Origin=nothing, StrikeAngle=0, DipAngle=0,
        phase = ConstantPhase(1).
        T=nothing, cell=false )
```

3Dモデルセットアップにフェーズと温度構造を持つ楕円体を追加します。これは、地球力学モデルにおけるモデルジオメトリの作成を簡素化します。

# パラメータ

  * `Phase` - フェーズ配列（グリッドと一致）
  * `Temp`  - 温度配列（グリッドと一致）
  * `Grid` - LaMEMグリッド構造（通常はread*LaMEM*inputfileで取得）
  * `cen` - 球の中心座標
  * `axes` - 楕円体の半軸（X,Y,Z）
  * `Origin` - ボックスを回転させるために使用される原点。デフォルトは左前上隅
  * `StrikeAngle` - スラブのストライク角
  * `DipAngle` - スラブのディップ角
  * `phase` - ボックスのフェーズを指定します。`ConstantPhase()`,`LithosphericPhases()`を参照
  * `T` - ボックスの温度を指定します。`ConstantTemp()`,`LinearTemp()`,`HalfspaceCoolingTemp()`,`SpreadingRateTemp()`を参照
  * `cell` - trueの場合、`Phase`と`Temp`はセルの中心で定義されます

# 例

定数のフェーズと温度を持つ楕円体で、90度回転し、45度傾斜させたもの：

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
julia> add_ellipsoid!(Phases,Temp,Grid, cen=(-1,-1,-1), axes=(0.2,0.1,0.5), StrikeAngle=90, DipAngle=45, phase=ConstantPhase(3), T=ConstantTemp(600))
julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Cartesianモデルを作成
julia> write_paraview(Model3D,"LaMEM_ModelSetup")           # モデルをparaviewに保存
1-element Vector{String}:
 "LaMEM_ModelSetup.vts"
```
