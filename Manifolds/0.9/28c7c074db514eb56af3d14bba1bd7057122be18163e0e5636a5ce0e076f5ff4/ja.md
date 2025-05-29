```
exp(M::Stiefel, p, X)
```

点 `p` から接ベクトル方向 `X` に発生する [`Stiefel`](@ref)`{n,k,𝔽}`() 多様体 `M` 上の指数写像を計算します。

$$
\exp_p X = \begin{pmatrix}
   p\\X
 \end{pmatrix}
 \operatorname{Exp}
 \left(
 \begin{pmatrix} p^{\mathrm{H}}X & - X^{\mathrm{H}}X\\
 I_n & p^{\mathrm{H}}X\end{pmatrix}
 \right)
\begin{pmatrix}  \exp( -p^{\mathrm{H}}X) \\ 0_n\end{pmatrix},
$$

ここで、$\operatorname{Exp}$ は行列指数関数を示し、$⋅^{\mathrm{H}}$ は複素共役転置またはエルミートを示し、$I_k$ と $0_k$ はそれぞれ次元 $k×k$ の単位行列とゼロ行列です。
