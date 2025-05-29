```julia
make*volc*topo(Grid::LaMEM_grid; center::Array{Float64, 1}, height::Float64, radius::Float64, crater::Float64,             base=0.0m, background=nothing)

一般的な火山の地形（円錐と切り取られた円錐）を作成します。

# パラメータ

  * Grid - LaMEMグリッド（read*LaMEM*inputfileによって作成）
  * center - 火山の中心のx座標とy座標
  * height - 火山の高さ
  * radius - 火山の半径

# オプションのパラメータ

  * crater - これにより切り取られた円錐が作成され、オプションは平らな頂部の半径を定義します
  * base - これにより火山の周りの平らな地形が設定されます
  * background - これにより地形を読み込み、その上に火山を追加することができます（異なる傾斜を持ついくつかの円錐を重ねることも可能です）

# 例

定数の相と温度を持つ円柱：

```

julia-repl julia> Grid = read*LaMEM*inputfile("test*files/SaltModels.dat") LaMEM Grid:   nel         : (32, 32, 32)   marker/cell : (3, 3, 3)   markers     : (96, 96, 96)   x           ϵ [-3.0 : 3.0]   y           ϵ [-2.0 : 2.0]   z           ϵ [-2.0 : 0.0] julia> Topo = make*volc*topo(Grid, center=[0.0,0.0], height=0.4, radius=1.5, crater=0.5, base=0.1) CartData     size    : (33, 33, 1)     x       ϵ [ -3.0 : 3.0]     y       ϵ [ -2.0 : 2.0]     z       ϵ [ 0.1 : 0.4]     fields  : (:Topography,)   attributes: ["note"] julia> Topo = make*volc*topo(Grid, center=[0.0,0.0], height=0.8, radius=0.5, crater=0.0, base=0.4, background=Topo.fields.Topography) CartData     size    : (33, 33, 1)     x       ϵ [ -3.0 : 3.0]     y       ϵ [ -2.0 : 2.0]     z       ϵ [ 0.1 : 0.8]     fields  : (:Topography,)   attributes: ["note"] julia> write*paraview(Topo,"VolcanoTopo")           # 地形をparaviewに保存 Saved file: VolcanoTopo.vts ```
