```
LinearKernel(; c::Real=0.0)
```

定数オフセット `c` を持つ線形カーネル。

# 定義

入力 $x, x' \in \mathbb{R}^d$ に対して、定数オフセット $c \geq 0$ を持つ線形カーネルは次のように定義されます。

$$
k(x, x'; c) = x^\top x' + c.
$$

関連項目: [`PolynomialKernel`](@ref)
