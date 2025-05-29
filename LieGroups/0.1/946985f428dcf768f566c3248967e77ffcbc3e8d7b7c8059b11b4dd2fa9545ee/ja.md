```
log(G::SpecialEuclidean, g)
log!(G::SpecialEuclidean, X, g)
```

[`SpecialEuclideanGroup`](@ref) `G`$=\mathrm{SE}(3)$ 上のリー群対数関数を計算します。ここで `e` は $\mathrm{SE}(3)$ の [`Identity`](@ref) であり、`G` はディスパッチのために [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`)`{Tuple{3}}` を使用します。

$$
g=(R,t) ∈ \mathrm{SE}(3)
$$

は回転成分 $R ∈ \mathrm{SO}(3)$ と平行移動成分 $t ∈ \mathcal T(2)$ から構成されるため、まず $Y = \log_{\mathrm{SO}(3)}R$ を計算します。次に、$\mathrm{SO}(3)$ 上の [`vee`](@ref) を使用して回転角 $α$ を取得できます（または $\sqrt{2}α = \lVert Y \rVert_{}$ を使用してもよいです）。

$$
α ≠ 0
$$

の場合、次のように定義します。

$$
V_α = I_3 - \frac{1}{2}Y + β Y^2, \quad\text{ ただし } β = \frac{1}{α^2} - \frac{1 + \cos(α)}{2α\sin(α)}
$$

$$
V_0 = I_3
$$

であり、ここで $I_3$ は単位行列です。これは、群の指数における $U_α$ の逆であることに注意してください。

したがって、結果 $X = (Y, v) ∈ \mathfrak se(3)$ は、上で計算した $Y ∈ \mathfrak so(3)$ と $v = V_α t ∈ \mathfrak t(3)$ によって与えられます。

この結果は `X` のインプレースで計算できます。
