```julia
triface_quadrature(N)

```

直角三角形の面に沿った数値積分点を計算します

  * 面 1: 1 -> 2
  * 面 2: 2 -> 3
  * 面 3: 3 -> 1

面 2 は斜辺であると仮定します

@arg N: 多項式の次数
