```
exp(G::SpecialEuclidean, X)
exp!(G::SpecialEuclidean, g, X)
```

[`SpecialEuclideanGroup`](@ref) `G`$=\mathrm{SE}(3)$ の上でリー群指数関数を計算します。ディスパッチのために [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`)`{Tuple{3}}` を使用します。

$$
X = (Y, v) ∈ \mathfrak se(3)
$$

は回転成分 $Y ∈ \mathfrak se(3)$ と平行移動成分 $v ∈ \mathfrak t(3)$ から構成されるため、回転角 $α$ を得るために [`vee`](@ref) を用いて $\mathrm{SO}(3)$ 上で係数のノルムを計算できます（または、$\sqrt{2}α = \lVert Y \rVert_{}$ を使用することもできます）。

$$
α ≠ 0
$$

の場合、次のように定義します。

$$
U_α = I_3 + \frac{1-\cosα}{α^2}Y + \frac{α-\sinα}{α^3}Y^2,
$$

そして $U_0 = I_3$ であり、$I_2$ は単位行列です。

その結果 $g=(R,t)$ は次のように与えられます。

$$
R = \exp_{\mathrm{SO}(3)}Y ∈ \mathrm{SO}(3),
\quad
\text{ and }
\quad
t = U_αv ∈ \mathcal T(3).
$$

この結果は `g` のインプレースで計算できます。
