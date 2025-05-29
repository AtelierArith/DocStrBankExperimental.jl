```
log(G, g)
log!(G, X, g)
```

[`OrthogonalGroup`](@ref) $\mathrm{O}(3)$ または [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(3)$ 上でのリー群対数関数を計算します。ここで `e` は [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` であり、`G` はディスパッチのために [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) を使用します。

ここで、$\exp_{\mathcal G}(X) = g$ は [ロドリゲスの回転公式](https://en.wikipedia.org/wiki/Olinde_Rodrigues) を使用して逆転されます。

$$
\exp_{\mathcal G}(X) = I_3 + \frac{\sin}{α}X + \frac{(1 - \cos)}{α^2}X^2,
$$

$$
α ∉ \{ 0, π \}
$$

の場合、次の観察から $X$ を得ます。

$$
\mathrm{tr}(g) = 1 + 2\cos(α)
\qquad\text{ および }\qquad
\frac{1}{2}(g-g^\mathrm{T}) = \sin(α)X.
$$

$$
α = 0
$$

の場合、$g = I_3$ であり、$X = 0$ です。

$$
α = π
$$

の場合、$X^2 = \frac{1}{2}(g-I_3)$ を解く必要があり、ここで $X$ は斜対称であるため、3つの未知数を解く必要があります。

$$
\log_{\mathcal G}(g) = X.
$$

この結果は `X` のインプレースで計算できます。

対数写像は、特に $\mathrm{O}(3)$ が2つの離散的な連結成分から成るため、単位元の周りでのみ一意に決定されることに注意してください。また、指数写像は滑らかであるため、他の成分の任意の $g$ に対して対数写像は定義されますが、指数写像の逆は定義されません。
