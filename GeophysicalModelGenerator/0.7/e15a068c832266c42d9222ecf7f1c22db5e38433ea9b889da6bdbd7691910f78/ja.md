```
add_stripes!(Phase, Grid::AbstractGeneralGrid;
    stripAxes       = (1,1,0),
    stripeWidth     =  0.2,
    stripeSpacing   =  1,
    Origin          =  nothing,
    StrikeAngle     =  0,
    DipAngle        =  10,
    phase           =  ConstantPhase(3),
    stripePhase     =  ConstantPhase(4),
    cell            = false)

事前に定義されたフェーズにストライプを追加します（例：add_box!を使用して追加）。

# パラメータ

  * `Phase` - フェーズ配列（Gridと一致）
  * `Grid` - グリッド構造（通常はread*LaMEM*inputfileで取得されますが、他のグリッドタイプでも可能）
  * `stripAxes` - ストライプを設定したい軸を指定します。デフォルトは(1,1,0)、すなわちX、Y、Zではない
  * `stripeWidth` - ストライプの幅
  * `stripeSpacing` - 2つのストライプ間のスペース
  * `Origin` - ボックスを回転させるために使用される原点。デフォルトは左前上隅
  * `StrikeAngle` - ストライク角
  * `DipAngle` - ディップ角
  * `phase` - ストライプを適用したいフェーズを指定
  * `stripePhase` - ストライプフェーズを指定
  * `cell` - trueの場合、`Phase`と`Temp`は中心で定義されます

# 例

例：ストライプのあるフェーズと一定の温度、ディップ角10度のボックス：

```

julia-repl julia> Grid = read*LaMEM*inputfile("test*files/SaltModels.dat") LaMEM Grid:   nel         : (32, 32, 32)   marker/cell : (3, 3, 3)   markers     : (96, 96, 96)   x           ϵ [-3.0 : 3.0]   y           ϵ [-2.0 : 2.0]   z           ϵ [-2.0 : 0.0] julia> Phases = zeros(Int32,   size(Grid.X)); julia> Temp   = zeros(Float64, size(Grid.X)); julia> add*box!(Phases,Temp,Grid, xlim=(0,500), zlim=(-50,0), phase=ConstantPhase(3), DipAngle=10, T=ConstantTemp(1000)) julia> add*stripes!(Phases, Grid, stripAxes=(1,1,1), stripeWidth=0.2, stripeSpacing=1, Origin=nothing, StrikeAngle=0, DipAngle=10, phase=ConstantPhase(3), stripePhase=ConstantPhase(4)) julia> Model3D = ParaviewData(Grid, (Phases=Phases,Temp=Temp)); # Cartesianモデルを作成 julia> write*paraview(Model3D,"LaMEM*ModelSetup")           # モデルをparaviewに保存 1-element Vector{String}:  "LaMEM*ModelSetup.vts" ```
