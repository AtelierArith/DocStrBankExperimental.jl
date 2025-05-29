```
fdiff_differentiation_expansion_polynom(σ::T [, k=5 [, notation=bwd]]) where T<:Real
```

有限差分展開係数ベクトルは、位置 $v=n-σ$ における表形式の解析関数 $f[n]$ の $k^{th}$-order *ラグランジュ微分* を定義します。

**前方差分表記** (`notation = fwd`)

$$
\frac{df}{dσ}[n+σ]=\sum_{p=0}^kα_p(σ)Δ^{p}f[n]
$$

オフセット規約: $σ = n-v$ は、表形式の区間 $f[n:n+k]$ におけるインデックス $n$ に関してです。

**後方差分表記** (`notation = bwd`)

$$
\frac{df}{dσ}[n+σ]=\sum_{p=0}^kβ_p(σ)∇^{p}f[n]
$$

ここで $β(σ) ≡ [β_0(σ),\ ⋯,\ β_p(σ)]$ です。

オフセット規約: $σ = -(n-v)$ は、表形式の区間 $f[n-k:n]$ におけるインデックス $n$ に関してです。

#### 例:

```
julia> k = 5; σ = 0; # 微分に対応するオフセット

julia> o = fdiff_differentiation_expansion_polynom(0, k, fwd); println(o)
Rational{Int64}[0, 1, -1//2, 1//3, -1//4, 1//5]
```
