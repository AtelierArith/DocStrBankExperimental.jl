```
ids = inwhichpolygon(point::Matrix{Real}, D::Vector{GMTdataset}; on_is_in=false, pack=false)
```

または

```
ids = inwhichpolygon(x, y, D::Vector{GMTdataset}; on_is_in=false, pack=false)
```

クエリポイント `point` を囲むポリゴンのIDを見つけます。行列 `point` の各行にはクエリポイントの座標が含まれています。どのポリゴンにも含まれないクエリポイントはID = 0になります。入力クエリポイントの数に応じて、$Int$ または $Vector{Int}$ を返します。

  * `D`: ポリゴンを定義するGMTdatasetのベクトル。
  * `point`: xおよびyのポイント座標を持つMx2行列または2要素ベクトル。
  * `x, y`: 2次元クエリポイントのx座標とy座標を別々のベクトル（または2つのスカラー）として指定します。
  * `on_is_in`: `on_is_in=true` の場合、境界上に正確にあるポイントは内部と見なされます。デフォルトは `false` です。
  * `pack`: `pack=true` の場合、ヒットしたポリゴンのIDと各ポリゴンにヒットしたクエリポイントのインデックスを持つベクトルのベクトルが返されます。つまり、ids[1] には少なくとも1つのヒットを受けた `D` のインデックスが含まれ、ids[2] にはポリゴン D[ids[1]] にヒットしたクエリ `point` のインデックスが含まれます。

### 例:

```
pts = [[1 2 3;1 2 3;1 2 3][:] [1 1 1;2 2 2; 3 3 3][:]];
D = triplot(pts, noplot=true);
points = [2.4 1.2; 1.4 1.4];
ids = inwhichpolygon(points, D);
# 三角形分割とクエリポイントをプロットします。
plot(D)
plot!(D[ids[1]], fill=:grey)
plot!(D[ids[2]], fill=:green)
plot!(points, marker=:star, ms="12p", fill=:blue, show=true)
```
