```
create_mesh(point :: Array{Float64,2}; <keyword arguments>)
```

点群の凸包の三角形分割を作成します。

# キーワード引数

  * `point_marker :: Array{Int,2} = Array{Int,2}(undef,0,size(point,1))`: 点にはマーカーを持たせることができます。
  * `point_attribute :: Array{Float64,2} = Array{Float64,2}(undef,0,size(point,1))`: 点には複数の属性を与えることができます。
  * `info_str :: String = "Triangular mesh of convex hull of point cloud."`: メッシュに関する情報
  * `verbose :: Bool = false`: 三角形の出力を印刷します
  * `check_triangulation :: Bool = false`: 作成後にDelaunay特性のために三角形分割をチェックします
  * `voronoi :: Bool = false`: Voronoi図を出力します
  * `delaunay :: Bool = false`: trueの場合、このオプションはメッシュが制約付きDelaunayではなくDelaunayであることを保証します。また、すべてのVoronoi頂点が三角形分割内にあることを保証したい場合にもtrueに設定できます。
  * `output_edges :: Bool = true`: trueの場合、エッジリストを提供します。
  * `output_cell_neighbors :: Bool = true`: trueの場合、各三角形の隣接三角形のリストを出力します
  * `quality_meshing :: Bool = true`: trueの場合、20度未満の角を持つ三角形を避けます
  * `prevent_steiner_points_boundary :: Bool = false`: trueの場合、境界セグメントにSteiner点は追加されません。
  * `prevent_steiner_points :: Bool = false`: trueの場合、内部セグメントの境界セグメントにSteiner点は追加されません。
  * `set_max_steiner_points :: Bool = false`: trueの場合、ユーザーに追加されるSteiner点の最大数を入力するよう求められます。ユーザーが0を入力した場合、これは`set_max_steiner_points = true`と同等です。
  * `set_area_max :: Bool = false`: trueの場合、ユーザーに最大三角形面積を尋ねます。
  * `set_angle_min :: Bool = false`: trueの場合、ユーザーに三角形分割における最小角の下限を尋ねます。
  * `add_switches :: String = ""`: ユーザーはtriangleのドキュメントに記載されている追加のスイッチを渡すことができます。このオプションは、何をしているかを理解している場合にのみ設定してください。
