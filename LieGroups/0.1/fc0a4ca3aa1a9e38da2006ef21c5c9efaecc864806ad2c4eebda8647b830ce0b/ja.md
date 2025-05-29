```
log(G::SpecialEuclidean, g)
log!(G::SpecialEuclidean, X, g)
```

[`SpecialEuclideanGroup`](@ref) `G`$=\mathrm{SE}(2)$ の上でリー群対数関数を計算し、`G` はディスパッチのために [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`)`{Tuple{2}}` を使用します。

$$
g=(R,t) ∈ \mathrm{SE}(2)
$$

は回転成分 $R ∈ \mathrm{SO}(2)$ と平行移動成分 $t ∈ \mathcal T(2)$ から構成されるため、まず $Y = \log_{\mathrm{SO}(2)}R$ を計算します。次に、$\mathrm{SO}(2)$ 上の [`vee`](@ref) を使用して回転角 $α$ を取得できます（または $\sqrt{2}α = \lVert Y \rVert_{}$ を使用してもよいです）。

$$
α ≠ 0
$$

の場合、次のように定義します。

$$
V_α = \frac{α}{2} \begin{pmatrix} \frac{\sinα}{1-\cosα} & 1\\ -1 & \frac{\sinα}{1-\cosα}\end{pmatrix}
$$

そして $V_0 = I_2$、ここで $I_2$ は単位行列です。これは、群の指数関数で与えられる $U_α$ の逆であることに注意してください。

次に、結果 $X = (Y, v) ∈ \mathfrak se(2)$ は、上で計算したように $Y ∈ \mathfrak so(2)$ によって与えられ、

$$
v = V_αr ∈ \mathcal T(2),
$$

ここで $v$ は $V_α$ を設定することなくインプレースで計算されます。

この結果は `g` のインプレースで計算できます。
