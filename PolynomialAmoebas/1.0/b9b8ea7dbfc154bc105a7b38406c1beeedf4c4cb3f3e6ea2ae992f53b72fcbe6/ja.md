```
NewtonPolygon
```

多項式の[ニュートン多角形](https://en.wikipedia.org/wiki/Newton_polygon)の表現。

## フィールド

  * `polynomial::P`: ニュートン多角形が構築された多項式。
  * `lattices::Vector{SVector{2,Int}}`: 多項式 `p` のサポート。
  * `vertices::Vector{Int}`: ニュートン多角形の頂点インデックス。
  * `facets::Vector{SVector{2,Int}}`: ニュートン多角形の面、すなわちその凸包。
  * `subdivision::Vector{SVector{3,Int}}`: ニュートン多角形の正則分割の単体。
