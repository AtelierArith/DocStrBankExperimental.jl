Nモードボソニックシステムのためのガウス状態を2N次元の位相空間で定義します。

## フィールド

  * `basis`: ガウス状態のシンプレクティック基底。
  * `mean`: 長さ2Nの平均ベクトル。
  * `covar`: サイズ2N x 2Nの共分散行列。
  * `ħ = 2`: 縮小プランク定数。

## 例

```jldoctest
julia> coherentstate(QuadPairBasis(1), 1.0+im)
GaussianState for 1 mode.
  symplectic basis: QuadPairBasis
mean: 2-element Vector{Float64}:
 2.0
 2.0
covariance: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
