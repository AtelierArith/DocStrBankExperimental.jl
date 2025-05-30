```
boxcox(λ; atol=0)
boxcox(λ, x; atol=0)
```

パラメータ値 λ に対する x のボックス-コックス変換を計算します。

ボックス-コックス変換は次のように定義されます：

$$
\begin{cases}
\frac{x^{\lambda} - 1}{\lambda} &\quad \lambda \neq 0 \\
\log x &\quad \lambda = 0
\end{cases}
$$

正の $x$ に対して。（もし $x <= 0$ の場合、$x$ はまず厳密に正になるように変換されなければなりません。）

`atol` は λ をゼロとして扱うための絶対許容誤差を制御します。

1 引数のバリアントはカリー化され、与えられた λ に対する `x` の 1 引数関数を作成します。

詳細は [`BoxCoxTransformation`](@ref) を参照してください。

# 参考文献

Box, George E. P.; Cox, D. R. (1964). "An analysis of transformations". *Journal of the Royal Statistical Society*, Series B. 26 (2): 211–252.
