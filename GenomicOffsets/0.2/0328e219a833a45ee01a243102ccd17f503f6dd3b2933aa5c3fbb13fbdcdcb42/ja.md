```
RidgeLFMM(Y::Matrix{T}, X::Matrix{T}, K::Int, λ::Float64) where T<:Real
```

Caye et al. (2019) によって説明された線形固定効果混合モデル (LFMM) のリッジ解。

$$
Y = X B^T + W = X B^T + U V^T
$$

# 引数

  * `Y`: サイズ NxL の中心化された遺伝子型行列。
  * `X`: サイズ NxP の環境行列。
  * `K`: 潜在因子の数。
  * `λ`: 正則化パラメータ (1e-5 による)
  * `center`: true の場合、遺伝子型行列と環境行列の両方が中心化されます。false の場合、両方の行列は中心化されていると見なされます。

# 戻り値

  * 潜在因子 `U`、`Vt`、および効果サイズ `Bt` を持つ `LFMM{T<:Real}` データ構造。
