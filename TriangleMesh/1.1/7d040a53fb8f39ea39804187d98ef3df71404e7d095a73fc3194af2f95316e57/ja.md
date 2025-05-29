```
refine(m :: TriMesh, switches :: String; <keyword arguments>)
```

ユーザーが設定した制約に従って三角形メッシュを細分化します。コマンドラインスイッチは直接渡されます。この関数は、何をしているかを理解している場合のみ使用してください。

# キーワード引数

  * `divide_cell_into :: Int = 4`: `ind_cell`にリストされた三角形は、細分化された三角形分割において1/divide*cell*into * area(triangle[ind_cell])によって面積が制約されます。
  * `ind_cell :: Array{Int,1} = collect(1:m.n_cell)`: 細分化される三角形のリスト。
  * `info_str :: String = "Refined mesh"`: 一部の情報文字列。
