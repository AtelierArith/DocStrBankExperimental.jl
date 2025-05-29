```
AsphericSurface{T,N,Q,M} <: ParametricSurface{T,N}
```

非球面多項式を組み込んだ表面 - 半径、円錐、および非球面は絶対半径に対して定義されます。`T` はデータ型、`N` は次元、`Q` は非球面項の数、`M` は非球面多項式の型です。

```julia
AsphericSurface(semidiameter; radius, conic, aspherics=nothing, normradius = semidiameter)
```

この表面は原点に中心を持ち、無限の円柱のキャップとして扱われるため、真の半空間を作成します。`0 <= ρ <= 1` の範囲外では、表面の高さは必ずしも明確に定義されないため、NaN が返される場合があります。

`aspherics` は、非球面項の多項式のべき乗を表す i とその値 v のタプルを含むベクトルであるべきです。空のベクトルは許可されていません。代わりに `nothing` を使用してください。

サグは次の方程式によって定義されます。

$$
z(r,\phi) = \frac{cr^2}{1 + \sqrt{1 - (1+k)c^2r^2}} + \sum_{i}^{Q}\alpha_ir^{i}
$$

ここで、$\rho = \frac{r}{\texttt{normradius}}$、$c = \frac{1}{\texttt{radius}}$、および $k = \texttt{conic}$ です。

この関数は、非球面項が欠落しているか、偶数、奇数、またはその両方であるかをチェックし、効率的な多項式評価戦略を使用します。
