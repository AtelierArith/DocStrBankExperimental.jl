```
QTypeSurface{T,D,M,N} <: ParametricSurface{T,D}
```

QType多項式を組み込んだサーフェス - 半径と円錐は絶対半径に対して定義され、QType項は`normradius`パラメータに従って正規化されます。`T`はデータ型、`D`は次元、`M`と`N`は使用される最大QType項です。

サーフェスは原点に中心を置き、無限の円柱のキャップとして扱われるため、真の半空間を作成します。0 <= ρ <= 1の外側では、サーフェスの高さは必ずしも明確に定義されていないため、NaNが返される場合があります。

```julia
QTypeSurface(semidiameter; radius = Inf, conic = 0.0, αcoeffs = nothing, βcoeffs = nothing, normradius = semidiameter)
```

`αcoeffs`と`βcoeffs`は、`v`が係数$α_n^m$または$β_n^m$の値である形式`(m, n, v)`のタプルのベクトルである必要があります。

サグは次の方程式によって定義されます。

$$
\begin{aligned}
z(r,\phi) = & \frac{cr^2}{1 + \sqrt{1 - (1+k)c^2r^2}} + \frac{\sqrt{1 + kc^2r^2}}{\sqrt{1-(1+k)c^2r^2}} \cdot \\
             & \left\{ \rho^2(1-\rho^2)\sum_{n=0}^{N}\alpha_n^0 Q_n^0 (\rho^2) + \sum_{m=1}^{M}\rho^m\sum_{n=0}^N \left[ \alpha_n^m\cos{m\phi} +\beta_n^m\sin{m\phi}\right]Q_n^m(\rho^2) \right\}
\end{aligned}
$$

ここで、$\rho = \frac{r}{\texttt{normradius}}$、$c = \frac{1}{\texttt{radius}}$、$k = \texttt{conic}$、および$Q_n^m$はQType多項式のインデックス$m$、$n$です。
