```
create_mesh(point :: Array{Float64,2}, switches :: String; <keyword arguments>)
```

平面直線グラフ (PSLG) ポリゴンの三角形分割を作成します。メッシングアルゴリズムのオプションは、Triangle のコマンドラインスイッチを介して直接渡されます。自分が何をしているか分かっている場合のみ使用してください。

# キーワード引数

  * `point_marker :: Array{Int,2} = Array{Int,2}(undef,0,size(point,1))`: ポイントにはマーカーを付けることができます。
  * `point_attribute :: Array{Float64,2} = Array{Float64,2}(undef,0,size(point,1))`: ポイントには複数の属性を付与することができます。
  * `info_str :: String = "Triangular mesh of convex hull of point cloud."`: メッシュに関する情報の一部です。
