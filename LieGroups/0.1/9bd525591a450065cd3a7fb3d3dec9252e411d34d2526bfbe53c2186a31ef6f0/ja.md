```
exp(G::SpecialEuclidean, X)
exp!(G::SpecialEuclidean, g, X)
```

[`SpecialEuclideanGroup`](@ref) `G`$=\mathrm{SE}(2)$上でリー群指数関数を計算します。ディスパッチのために[`TypeParameter`](@extref `ManifoldsBase.TypeParameter`)`{Tuple{2}}`を使用します。

リー代数ベクトル $X = (Y, v) ∈ \mathfrak se(2)$ は、回転成分 $Y ∈ \mathfrak so(2)$ と平行移動成分 $v ∈ \mathfrak t(2)$ から構成されるため、$\mathrm{SO}(2)$上の[`vee`](@ref)を使用して回転角 $α$ を取得できます（または、$\sqrt{2}α = \lVert Y \rVert_{}$を使用することもできます）。

$$
α ≠ 0
$$

の場合、次のように定義します。

$$
U_α = \frac{\sinα}{α}I_2 + \frac{1-\cosα}{α^2}Y,
$$

そして $U_0 = I_2$、ここで $I_2$ は単位行列です。

すると、結果 $g=(R,t)$ は次のように与えられます。

$$
R = \exp_{\mathrm{SO}(2)}Y ∈ \mathrm{SO}(2),
\quad
\text{ および }
\quad
t = U_αv ∈ \mathcal T(2).
$$

この結果は `g` のインプレースで計算できます。
