```
broomhead_king(s::AbstractVector, d::Int) -> U, S, Vtr
```

時系列 `s` の Broomhead-King 座標を、最小遅延で次元 `d` の高次元遅延埋め込みに対して `svd` を実行することによって返します。

## 説明

Broomhead と King の座標は、最小の遅延を持つ遅延座標埋め込みに Karhunen–Loève 定理を適用することを提案したアプローチです [^Broomhead1987]。

この関数は、$s$ の `d` 次元行列 $X$ に対して特異値分解を行います。

$$
X = \frac{1}{\sqrt{N}}\left(
\begin{array}{cccc}
x_1 & x_2 & \ldots & x_d \\
x_2 & x_3 & \ldots & x_{d+1}\\
\vdots & \vdots & \vdots & \vdots \\
x_{N-d+1} & x_{N-d+2} &\ldots & x_N
\end{array}
\right) = U\cdot S \cdot V^{tr}.
$$

ここで $x := s - \bar{s}$ です。$U$ の列は新しい座標系として使用でき、特異値 $S$ の値を考慮することで、$U$ のどの列が「重要」であるかを決定できます。

[^Broomhead1987]: Broomhead, Jones, King, J. Phys. A **20**, 9, pp L563 (1987)
