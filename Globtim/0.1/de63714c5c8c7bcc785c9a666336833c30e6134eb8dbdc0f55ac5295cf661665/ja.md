```
struct ApproxPoly
```

多項式近似と関連データを表す構造体です。

# フィールド

  * `coeffs::Vector`: 多項式近似の係数。浮動小数点数または大きな有理数である可能性があります。  _ `degree::Int`: 多項式近似の次数。
  * `nrm::Float64`: 多項式近似のノルム。
  * `N::Int`: 近似に使用されるグリッドポイントの数。
  * `scale_factor::Float64`: ドメインに適用されるスケーリングファクター。
  * `grid::Matrix{Float64}`: 近似に使用されるポイントのグリッド。
  * `z::Vector{Float64}`: グリッドポイントでの目的関数の値。

# 説明

`ApproxPoly` 構造体は、多項式の係数、近似のノルム、グリッドポイントの数、スケーリングファクター、ポイントのグリッド、およびグリッドポイントでの関数の値を含む多項式近似の結果を格納するために使用されます。
