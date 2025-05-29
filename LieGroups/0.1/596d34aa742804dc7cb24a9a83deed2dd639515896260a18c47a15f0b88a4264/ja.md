```
log(G, g)
log!(G, X, g)
```

[`OrthogonalGroup`](@ref) $\mathrm{O}(2)$ または [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(2)$ 上でのリー群対数関数を計算します。ここで `e` は [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` であり、`G` はディスパッチのために [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) を使用します。

二次元の場合、任意の回転行列 $g$ は $\begin{pmatrix} \cos(α) & -\sin(α)\\ \sin(α) & \cos(α)\end{pmatrix}$ として表現できます。[`SpecialOrthogonalGroup`](@ref) の場合、$g$ は反射を含むこともあります。

対数は次のようになります。

$$
\log_{\mathcal G}(g) =  \begin{pmatrix} 0 & α\\ -α & 0\end{pmatrix}.
$$

この結果は `X` のインプレースで計算できます。

対数写像は、特に $\mathrm{O}(2)$ が二つの離散的な連結成分から成るため、単位元の周りでのみ一意に決定されることに注意してください。特に、他の成分の任意の $g$ に対して、対数写像は定義されますが、指数写像の逆は定義されません。
