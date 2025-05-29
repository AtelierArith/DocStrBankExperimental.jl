```
ChebyshevSurface{T,N,P,Q} <: ParametricSurface{T,N}
```

チェビシェフ多項式と半径および円錐項を組み込んだ長方形の表面。`T` はデータ型、`N` は次元、`P` は u におけるチェビシェフ項の数、`Q` は v におけるチェビシェフ項の数です。

この表面は原点を中心に配置されており、無限の長方形プリズムのキャップとして扱われるため、真の半空間を作成します。**表面は垂直にオフセットされており、中心（すなわち、`(u,v) == (0,0)`）が z 軸の 0 に位置することに注意してください。**

```julia
ChebyshevSurface(halfsizeu, halfsizev, chebycoeff; radius = Inf, conic = 0)
```

`chebycoeff` は、`(i, j, v)` の形のタプルを含むベクトルであり、ここで `v` は係数 $c_{ij}$ の値です。

サグは次の式で定義されます。

$$
z(u,v) = \frac{c(u^2 + v^2)^2}{1 + \sqrt{1 - (1+k)c^2(u^2 + v^2)}} + \sum_{i}^{P}\sum_{j}^{Q}c_{ij}T_i(u)T_j(v)
$$

ここで $c = \frac{1}{\texttt{radius}}$、$k = \texttt{conic}$ および $T_n$ は第一種の nᵗʰ チェビシェフ多項式です。
