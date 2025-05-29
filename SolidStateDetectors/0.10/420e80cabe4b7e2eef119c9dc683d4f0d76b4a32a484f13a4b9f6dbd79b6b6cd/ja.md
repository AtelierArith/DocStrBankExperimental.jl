```
struct NBodyChargeCloud{T, N, SH} <: AbstractChargeCloud
```

複数の点状電荷キャリアからなる電荷雲を定義する構造体で、初めは与えられた中心の周りに分布しています。

## パラメトリック型

  * `T`: 精度型。
  * `N`: シェルの数。
  * `SH`: シェルの幾何学。

## フィールド

  * `locations::Vector{CartesianPoint{T}}`: 電荷雲の一部である電荷キャリアの位置。
  * `energies::Vector{T}`: `locations`と同じ順序でのそれぞれの電荷キャリアのエネルギー。
  * `shell_structure::SH`: プロットに関連する`center`点の周りの電荷キャリアの初期幾何学。
