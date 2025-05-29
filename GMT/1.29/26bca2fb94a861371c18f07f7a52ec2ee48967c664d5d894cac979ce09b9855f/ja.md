```
in = inpolygon(x, y, polygon)
```

または

```
in = inpolygon(point, polygon)
```

`in`を返し、`x`と`y`で指定されたクエリポイントが以下で定義されたポリゴン領域内にあるかどうかを示します：

  * `polygon`: ポリゴンを定義するGMTデータセットまたは最初と最後の要素が等しい必要があるMx2の実数行列。
  * `point`: Mx2の行列またはxおよびyのポイント座標を持つ2要素のベクトル。`point`内のクエリポイントの数に応じて、$Int$または$Vector{Int}$のいずれかを返します。

## 戻り値:

  * in = 1
  * on = 0
  * out = -1

## 参考文献

  * Hao et al. 2018. [Optimal Reliable Point-in-Polygon Test and Differential Coding Boolean Operations on Polygons](https://www.mdpi.com/2073-8994/10/10/477)
