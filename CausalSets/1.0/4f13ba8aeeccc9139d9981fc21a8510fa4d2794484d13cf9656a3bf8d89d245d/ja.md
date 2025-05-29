```
HypercylinderManifold{N}(α::Float64) <: ConformallyHypercylindericalManifold{N}
```

多様体 $\mathbb{R} \times S^{N-1}$、ここで $S^{N-1}$ は $N-1$ 次元の球面です。パラメータ `α` は、この多様体が単位ハイパーシリンダーに対してのスケーリングファクターです。

座標タプルは $(t, θ_1, \cdots, θ_{N-1})$ であり、$θ_i$ は次のように $\mathbb{R}^N$ への $S^{N-1}$ の埋め込みによって定義される標準的な球面座標です：

$$
\begin{aligned}
x_1 &= \cos(θ_1) \\
x_2 &= \sin(θ_1) \cos(θ_2) \\
x_3 &= \sin(θ_1) \sin(θ_2) \cos(θ_3) \\
&\vdots \\
x_{N-1} &= \sin(θ_1) \cdots \sin(θ_{N-2}) \cos(θ_{N-1}) \\
x_N &= \sin(θ_1) \cdots \sin(θ_{N-2}) \sin(θ_{N-1})
\end{aligned}
$$

角度 $θ_1$ から $θ_{N-2}$ は $[0, \pi]$ の範囲にあり、$θ_{N-1}$ は $[0, 2\pi)$ の範囲にあります。

メトリックは次のようになります：

$$
\begin{aligned}
\mathrm{d} s^2 = - \alpha^2 \left( - \mathrm{d} t^2 + \mathrm{d} Ω_{N-1}^2 \right)
\end{aligned}
$$

ここで $\mathrm{d} Ω_{N-1}^2$ は $N - 1$ 次元の球面上の標準的な線要素です。
