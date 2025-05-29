```
refine(m :: TriMesh ; <keyword arguments>)
```

ユーザーが設定した制約に従って三角形メッシュを細分化します。

# キーワード引数

  * `divide_cell_into :: Int = 4`: `ind_cell`にリストされた三角形は、細分化された三角形において1/divide*cell*into * area(triangle[ind_cell])によって面積制約を受けます。
  * `ind_cell :: Array{Int,1} = collect(1:m.n_cell)`: 細分化される三角形のリスト。
  * `keep_segments :: Bool = false`: 入力三角形分割のセグメントを保持します（分割される可能性がありますが）。
  * `keep_edges :: Bool = false`: 入力三角形分割のエッジを保持します（分割される可能性がありますが）。
  * `verbose :: Bool = false`: 三角形のコマンドライン情報を出力します。
  * `check_triangulation :: Bool = false`: 細分化されたメッシュをチェックします。
  * `voronoi :: Bool = false`: ボロノイ図を出力します。
  * `output_edges :: Bool = true`: エッジを出力します。
  * `output_cell_neighbors :: Bool = true`: セルの隣接情報を出力します。
  * `quality_meshing :: Bool = true`: 角度が20度未満になることはありません。
  * `info_str :: String = "Refined mesh"`: 一部の情報文字列。

# 注記

`keep_segments`と`keep_edges`のスイッチは同時にtrueにすることはできません。`keep_segments=true`の場合、`ind_cell`にリストされた三角形に対する面積制約は、元のエッジが保持されない可能性があるため、三角形に対する厳しい制約ではなく、むしろ局所的な制約となります。詳細についてはTriangleのドキュメントを参照してください。
