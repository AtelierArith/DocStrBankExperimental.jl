Nモードボソニックシステムのためのガウスチャネルを2N次元の位相空間で定義します。

## フィールド

  * `basis`: ガウスチャネルのシンプレクティック表現。
  * `disp`: 長さ2Nの変位ベクトル。
  * `transform`: サイズ2N x 2Nの変換行列。
  * `noise`: サイズ2N x 2Nのノイズ行列。
  * `ħ = 2`: 簡約プランク定数。

## ガウスチャネルの数学的説明

Nモードガウスチャネルは、長さ2Nの変位ベクトル`d`、およびサイズ2N x 2Nの変換行列`T`とノイズ行列`N`によって特徴付けられる演算子であり、その作用がガウス状態に対してガウス状態を生成します。より具体的には、ガウス状態に対するガウスチャネルの作用は、ガウス状態の統計的モーメント`x̄`と`V`に対する写像によって記述されます：`x̄ → Tx̄ + d`および`V → TVTᵀ + N`。

## 例

```jldoctest
julia> noise = [1.0 -3.0; 4.0 2.0];

julia> displace(QuadPairBasis(1), 1.0+im, noise)
GaussianChannel for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 2.0
 2.0
transform: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
noise: 2×2 Matrix{Float64}:
 1.0  -3.0
 4.0   2.0
```
