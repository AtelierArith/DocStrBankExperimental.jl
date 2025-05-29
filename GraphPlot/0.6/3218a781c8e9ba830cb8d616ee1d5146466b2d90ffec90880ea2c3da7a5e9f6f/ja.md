この関数は[IainNZ](https://github.com/IainNZ)の[GraphLayout.jl](https://github.com/IainNZ/GraphLayout.jl)からコピーしたものです。

FruchtermanとReingold（1991）の春/反発モデルの修正版を使用しています：

  * 引力:  f_a(d) =  d / k
  * 反発力:  f_r(d) = -k^2 / d^2

ここで、dは2つの頂点間の距離であり、頂点間の最適距離kはC * sqrt( area / num_vertices )として定義され、Cは調整可能なパラメータです。

**パラメータ**

*g* グラフ

*C* 結果のレイアウトの密度を調整するための定数

*MAXITER* 力を適用する反復回数

*INITTEMP* 初期「温度」、反復ごとの移動を制御します

*seed* 位置の擬似乱数生成のための整数シード（デフォルト = 0）。

**例**

```
julia> g = smallgraph(:karate)
julia> locs_x, locs_y = spring_layout(g)
```
