```
create_mesh(poly :: Polygon_pslg; <keyword arguments>)
```

平面直線グラフ (PSLG) ポリゴンの三角形分割を作成します。

# キーワード引数

  * `info_str :: String = "ポリゴン (PSLG) の三角形メッシュ"`: メッシュに関する情報
  * `verbose :: Bool = false`: 三角形の出力を印刷
  * `check_triangulation :: Bool = false`: 作成後に Delaunay 特性のために三角形分割をチェック
  * `voronoi :: Bool = false`: ボロノイ図を出力
  * `delaunay :: Bool = false`: true の場合、このオプションはメッシュが制約付き Delaunay ではなく Delaunay であることを保証します。また、すべてのボロノイ頂点が三角形分割内にあることを保証したい場合にも true に設定できます。
  * `mesh_convex_hull :: Bool = false`: `poly` の凸包をメッシュ化します（ポリゴンが有界領域を囲まない場合に便利ですが、その凸包は囲みます）
  * `output_edges :: Bool = true`: true の場合、エッジリストを提供します。
  * `output_cell_neighbors :: Bool = true`: true の場合、各三角形の隣接三角形のリストを出力します
  * `quality_meshing :: Bool = true`: true の場合、20度未満の角を持つ三角形を避けます
  * `prevent_steiner_points_boundary :: Bool = false`: true の場合、境界セグメントにスティーナーポイントが追加されません。
  * `prevent_steiner_points :: Bool = false`: true の場合、内部セグメントの境界セグメントにスティーナーポイントが追加されません。
  * `set_max_steiner_points :: Bool = false`: true の場合、ユーザーに追加されるスティーナーポイントの最大数を入力するように求められます。ユーザーが 0 を入力した場合、これは `set_max_steiner_points = true` と同等です。
  * `set_area_max :: Bool = false`: true の場合、ユーザーに最大三角形面積を尋ねます。
  * `set_angle_min :: Bool = false`: true の場合、ユーザーに三角形分割の最小角度の下限を尋ねます。
  * `add_switches :: String = ""`: ユーザーは、triangle のドキュメントに記載されている追加のスイッチを渡すことができます。このオプションは、何をしているかを理解している場合にのみ設定してください。
