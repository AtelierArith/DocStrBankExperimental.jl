```
ZernikeSurface{T,N,P,Q,M} <: ParametricSurface{T,N}
```

Zernike多項式を組み込んだサーフェス - 半径、円錐および非球面は絶対半径に対して定義され、Zernike項は`normradius`パラメータに従って正規化されます。`T`はデータ型、`N`は次元、`P`はZernike項の数、`Q`は非球面項の数、`M`は非球面タイプです。

サーフェスは原点を中心に配置され、無限の円柱のキャップとして扱われるため、真の半空間を作成します。`0 <= ρ <= 1`の範囲外では、サーフェスの高さは必ずしも明確に定義されないため、NaNが返される場合があります。

便利のために、入力`zcoeff`は、`indexing`引数を使用して`ZernikeIndexingOSA`または`ZernikeIndexingNoll`のいずれかで示されるOSAまたはNoll規約を使用してインデックス付けできます。

```julia
ZernikeSurface(semidiameter, radius = Inf, conic = 0, zcoeff = nothing, aspherics = nothing, normradius = semidiameter, indexing = ZernikeIndexingOSA)
```

`zcoeff`と`aspherics`は、`i`が対応する`indexing`のZernike項のインデックスであるか、非球面項の多項式の次数（偶数または奇数の可能性あり）であり、`v`が対応する係数$A_i$または$\alpha_i$である形式のタプル`(i, v)`を含むベクトルである必要があります。`M`は、非球面多項式の評価を最適化するために入力された項から決定されます。

サグは次の方程式によって定義されます。

$$
z(r,\phi) = \frac{cr^2}{1 + \sqrt{1 - (1+k)c^2r^2}} + \sum_{i}^{Q}\alpha_ir^{2i} + \sum_{i}^PA_iZ_i(\rho, \phi)
$$

ここで、$\rho = \frac{r}{\texttt{normradius}}$、$c = \frac{1}{\texttt{radius}}$、$k = \texttt{conic}$、および$Z_n$はnᵗʰ Zernike多項式です。
