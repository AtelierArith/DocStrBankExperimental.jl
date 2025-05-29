グラフ `g` を `layout` の座標を使用して描画し、Luxor の `boundingbox` に収めます（デフォルトでは現在の描画の範囲に収まります）。

描画されたグラフの頂点の位置を示すポイントのベクトルを返します。

## キーワード引数

```
boundingbox::BoundingBox        グラフはこの BB の中に収まります
layout                          Point[] または関数
margin                          デフォルト 30
edgelist                        これらのエッジのみを描画

vertexfunction(vtx, coords) ->  頂点を描画
edgefunction(edgenumber, edgesrc, edgedest, from, to) -> エッジを描画
```

`layout`

  * 使用するレイアウト方法または座標。例：

```
layout = squaregrid

layout = shell

layout = vcat(
    [between(O + (-W / 2, -H / 2), O + (-W / 2, H / 2), i) for i in range(0, 1, length=N)], # 左
    [between(O + (W / 2, H / 2), O + (W / 2, -H / 2), i) for i in range(0, 1, length=N)] # 右
    )

layout = stress

layout = (g) -> spectral(adjacency_matrix(g), dim=2)

layout = shell ∘ adjacency_matrix

layout = (g) -> sfdp(g, Ptype=Float64, dim=2, tol=0.05, C=0.4, K=2)

layout = Shell(nlist=[6:10,]) # 頂点 6 から 10 の内部シェル

layout = squaregrid

the_positions = [(pt.x, pt.y) for pt in randompointarray(BoundingBox(), 50)[1:nv(G)]]
the_weights = rand(1:20, nv(G), nv(G))
layout=Stress(initialpos = the_positions,
    iterations = 30,
    weights = the_weights)

layout = Stress(iterations = 100, weights = M) # M は重みの行列

layout = Spring(iterations = 200, initialtemp = 2.5)
```

詳細については、NetworkLayout.jl のドキュメントを参照してください。

# 拡張ヘルプ

すべてのキーワード：

```plain
 boundingbox                 BoundingBox
 margin                      Number
 layout                      Vector{Point}
                             NetworkLayout.jl からの関数
                             f(g::Graph)
 edgefunction                f(edgenumber::Int, edgesrc::Int, edgedest::Int, from::Point)
 vertexfunction              f(vtx::Int, coordinates::Vector{Point})
 edgearrows                  :none
                             Boolean - 終端矢印を描画
                             Vector
                             f(edgenumber::Int, edgesrc::Int, edgedest::Int, from::Point)
                             - 関数は edgegaps をオーバーライドします
 edgecurvature               Float64
 edgedashpatterns            Vector{Vector}[number]
                             Vector{Number}
 edgegaps                    Vector
                             Range
                             Real
                             f(edgenumber::Int, edgesrc::Int, edgedest::Int, from::Point)
 edgelabelcolors             Vector{Colorant}
                             Colorant
 edgelabelfontfaces          Vector{Strings}[edgenumber]
                             String
                             :none
 edgelabelfontsizes          Vector{Number}
                             Number
 edgelabelrotations          Vector{angles}
                             angle::Float64
                             f(edgenumber, edges, edgedest, from, to)
 edgelabels                  Vector
                             range
                             Dict{Int, Int}
                             f(edgenumber, edgesrc, edgedest, from::Point, to::Point)
                               - この関数は必要なテキストを描画しなければなりません
                             :none
 edgelines                   Vector{Int}
                             range
                             Int
                             f(edgenumber, edgesrc, edgedest, from::Point, to::Point)
 edgelist                    Graphs.EdgeIterator
 edgestrokecolors            Vector{Colorant}[edge::Int]
                             Colorant
                             f(edgenumber, edgesrc, edgedest, from::Point, to::Point)
 edgestrokeweights           Vector{Number}[vtx]
                             range
                             Real
                             f(edgenumber, edgesrc, edgedest, from::Point, to::Point)
 vertexfillcolors            Vector{Colorant}
                             Colorant
                             :none
                             f(vtx::Int)
 vertexlabelfontfaces        Vector{Strings}
                             String
 vertexlabelfontsizes        Vector
                             range
                             Real
                             :none
                             f(vtx::Int, coord::Point[])
                              - 関数はフォントサイズの数値を返さなければなりません
 vertexlabeloffsetangles     Vector
                             Range
                             Real
 vertexlabeloffsetdistances  Vector
                             range
                             Real
 vertexlabelrotations        Vector
                             range
                             Real
                             :none
 vertexlabels                Vector{String}
                             String
                             range[vtx::Int]
                             :none
                             f(vtx::Int)
                             - この関数は文字列を返さなければなりません
 vertexlabeltextcolors       Vector{Colorant}
                             Colorant
                             f(vtx::Int)
                             :none
 vertexshaperotations        f(vtx::Int)
                             angle::Float64
 vertexshapes                Vector of :circle :square :none
                             range[vtx]
                             :circle :square :none
                             f(vtx::Int)
 vertexshapesizes            Vector{Real}
                             range
                             Real
                             :none
                             f(vtx::Int)
 vertexstrokecolors          Vector
                             Colorant
                             :none
                             f(vtx::Int)
 vertexstrokeweights         Vector
                             range
                             :none
                             f(vtx::Int)
```
