```
DeSitterManifold{N}(α::Float64) <: ConformallyHypercylindricalManifold{N}
```

1つの時間座標と $N - 1$ の空間座標を持つデシッターマンifoldです。パラメータ `α` はハイパーボロイド埋め込みに対するスケーリング因子です。座標 $N$-タプルは $(η, θ_i)$ であり、ここで $η$ は準同型時間で、$θ_i$ はデシッターマンifoldの時空間スライスをパラメータ化する $N - 1$ の球面角です。$N - 1$-球座標系は [`HypercylinderManifold`](@ref) の場合と同じです。

この多様体は、$x_μ x^μ = α^2$ を満たす $1 + N$ 次元ミンコフスキー時空の部分多様体として定義できます。これは、角度 $(ξ, θ_i)$ でパラメータ化された1シートのハイパーボロイドです：

$$
\begin{aligned}
x_0 &= α \sinh(ξ) \\
x_i &= α \cosh(ξ) X_i
\end{aligned}
$$

ここで、$X_i, 1 \leq i \leq N$ は球面角 $θ_i, 1 \leq i \leq N - 1$ に対応する単位 $N$-球座標です。この座標系の誘導計量は次のようになります：

$$
\begin{aligned}
\mathrm{d} s^2  = - α^2 (\mathrm{d} ξ^2 + \cosh^2(ξ) \mathrm{d} Ω_{N-1}^2)
\end{aligned}
$$

ここで、$\mathrm{d} Ω_{N-1}^2$ は $N - 1$-球上の標準的な線要素です。

次に、時間座標を *準同型時間* $η$ に再パラメータ化できます：

$$
\begin{aligned}
\cosh(ξ) = \frac{1}{\cos(η)}
\end{aligned}
$$

そのため、計量はハイパーシリンダー計量と準同型的に等価になります：

$$
\begin{aligned}
\mathrm{d} s^2  = \frac{α^2}{\cos^2(η)} \left( - \mathrm{d} ξ^2 + \mathrm{d} Ω_{N-1}^2 \right)
\end{aligned}
$$

準同型時間 $η$ は $-π/2$ から $π/2$ までの範囲です。
