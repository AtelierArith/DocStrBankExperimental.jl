Nモードボソニックシステムの2N次元位相空間におけるガウスユニタリを定義します。

## フィールド

  * `basis`: ガウスユニタリのシンプレクティック基底。
  * `disp`: 長さ2Nの変位ベクトル。
  * `symplectic`: サイズ2N x 2Nのシンプレクティック行列。
  * `ħ = 2`: 簡約プランク定数。

## ガウスユニタリの数学的説明

Nモードガウスユニタリは、長さ2Nの変位ベクトル`d`とサイズ2N x 2Nのシンプレクティック行列`S`によって特徴付けられるユニタリ演算子であり、その作用がガウス状態に対してガウス状態を生成します。より具体的には、ガウス状態に対するガウスユニタリ変換は、ガウス状態の統計的モーメント`x̄`と`V`に対する写像によって記述されます：`x̄ → Sx̄ + d`および`V → SVSᵀ`。

## 例

```jldoctest
julia> displace(QuadPairBasis(1), 1.0+im)
GaussianUnitary for 1 mode.
  symplectic basis: QuadPairBasis
displacement: 2-element Vector{Float64}:
 2.0
 2.0
symplectic: 2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
