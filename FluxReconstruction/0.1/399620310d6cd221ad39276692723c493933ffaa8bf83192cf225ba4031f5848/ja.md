```julia
tri_quadrature(deg; vertices, transform)

```

三角形の数値積分点を計算します

@arg deg: 多項式の次数 @arg vertices: 頂点の座標

  * 正三角形の場合、頂点は ([-1.0, -1 / √3], [1.0, -1 / √3], [0.0, 2 / √3]) です
  * 直角三角形の場合、頂点は ([-1.0, -1.0], [1.0, -1.0], [-1.0, 1.0]) です

@arg transform が true の場合、座標を x-y 平面から r-s 平面に変換します
