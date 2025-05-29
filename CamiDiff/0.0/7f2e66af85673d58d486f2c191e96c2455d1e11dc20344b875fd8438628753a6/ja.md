```
fdiff_expansion_weights(polynom [, notation=bwd [, ordering=rev]])
```

ユーザー定義の有限差分展開の展開係数ベクトル `polynom` に対応する重みベクトル。

**前方差分表記** (`notation = fwd`)

重みベクトル $F^k ≡ [F_k^k,⋯\ F_0^k]$ は、$k^{th}$-order *前方差分* 展開の展開係数ベクトル $α ≡ [α_0,⋯\ α_k]$ に対応します（`polynom = α`）。

$$
\sum_{p=0}^{k}α_{p}Δ^{p}f[n]
=\sum_{j=0}^{k}F_{j}^{k}f[n+j]
=F^{k} \cdot f[n:n+k],
$$

ここで $f[n:n+k]$ は、通常の*前方*順序で表された解析関数 $f$ の要素です。

[`fdiff_expansion_weights(α, fwd, reg)`](@ref) $→ F^k ≡ [F_0^k,⋯\ F_k^k]$,

ここで $α ≡ [α_0,⋯\ α_k]$ は、重みが前方差分表記で評価されることを示すために、ユーザーによって `fwd` と組み合わせて提供される必要があります。

**後方差分表記** (`notation = bwd`)

重みベクトル $\bar{B}^{k} ≡ [B_k^k,⋯\ B_0^k]$ は、$k^{th}$-order *後方差分* 展開の展開係数ベクトル $β ≡ [β_0,⋯\ β_k]$ に対応します（`polynom = β`）。

$$
\sum_{p=0}^{k}β_{p}∇^{p}f[n]
=\sum_{j=0}^{k}B_{j}^kf[n-j]
=\bar{B}^k \cdot f[n-k:n].
$$

ここで $f[n-k:n]$ は、*前方*順序で表された解析関数 $f$ の要素です。

[`fdiff_expansion_weights(β, bwd, rev)`](@ref) $→ \bar{B}^{k} ≡ [B_k^k,⋯\ B_0^k]$,

ここで $β ≡ [β_0,⋯\ β_k]$ は、重みが後方差分表記で評価されることを示すために、ユーザーによって `bwd` と組み合わせて提供される必要があります。

#### 例:

展開を考慮します。

$$
\begin{aligned}
f[n-1]=(1+Δ)^{-1}f[n]=(1-Δ+Δ^2-Δ^3+⋯)f[n]&=F^{k} \cdot f[n:n+k],\\
f[n+1]=(1-∇)^{-1}f[n]=(1+∇+∇^2+∇^3+⋯)f[n]&=\bar{B}^k \cdot f[n-k:n].
\end{aligned}
$$

```
julia> f = [0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100];

julia> α = [1,-1,1,-1,1];

julia> Fk = fdiff_expansion_weights(α, fwd, reg); println("Fk = $(Fk)")
Fk = [5, -10, 10, -5, 1]

julia> β = [1,1,1,1,1];

julia> revBk = fdiff_expansion_weights(β, bwd, rev); println("revBk = $(revBk)")
revBk = [1, -5, 10, -10, 5]

julia> Fk ⋅ f[7:11]
25

julia> revBk ⋅ f[1:5]
25

julia> f[6]
25
```
