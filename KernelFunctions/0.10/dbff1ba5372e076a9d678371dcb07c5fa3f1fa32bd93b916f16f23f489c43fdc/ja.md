```
PolynomialKernel(; degree::Int=2, c::Real=0.0)
```

次数 `degree` の定数オフセット `c` を持つ多項式カーネル。

# 定義

入力 $x, x' \in \mathbb{R}^d$ に対して、定数オフセット $c \geq 0$ を持つ次数 $\nu \in \mathbb{N}$ の多項式カーネルは次のように定義されます。

$$
k(x, x'; c, \nu) = (x^\top x' + c)^\nu.
$$

関連情報: [`LinearKernel`](@ref)
