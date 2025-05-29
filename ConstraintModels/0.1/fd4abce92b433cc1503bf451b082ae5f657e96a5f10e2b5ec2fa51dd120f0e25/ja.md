```
mincut(graph::AbstractMatrix{T}; source::Int, sink::Int, interdiction::Int = 0) where T <: Number
```

グラフの最小カットを計算します。

# 引数:

  * `graph`: グラフの容量を記述する任意の行列 <: AbstractMatrix
  * `source`: ソースノードのID; 設定する必要があります
  * `sink`: シンクノードのID; 設定する必要があります
  * `interdiction`: 禁止されたリンクの数を示します
