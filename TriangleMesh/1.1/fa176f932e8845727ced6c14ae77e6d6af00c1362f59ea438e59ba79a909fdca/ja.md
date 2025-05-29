```
polygon_struct_from_points(point :: Array{Float64,2},
                                pm :: Array{Int,2},
                                pa :: Array{Float64,2})
```

点の集合からポリゴンを作成します（例のコード）。ここではセグメントや穴は設定されていません。

# 引数

  * `point :: Array{Float64,2}`: 点の集合（次元 n-by-2）
  * `pm :: Array{Int,2}`: 各点にはマーカーを持つことができます（次元は n-by-0 または n-by-1）
  * `pa :: Array{Float64,2}`: 各点には $k>=0$ の実属性を持つことができます（次元 n-by-k）
