```
RationalKernel(; α::Real=2.0, metric=Euclidean())
```

形状パラメータ `α` と指定された `metric` を持つ有理カーネル。

# 定義

入力 $x, x'$ と距離 $d(\cdot, \cdot)$ に対して、形状パラメータ $\alpha > 0$ を持つ有理カーネルは次のように定義されます。

$$
k(x, x'; \alpha) = \bigg(1 + \frac{d(x, x')}{\alpha}\bigg)^{-\alpha}.
$$

デフォルトでは、$d$ はユークリッド距離 $d(x, x') = \|x - x'\|_2$ です。

[`ExponentialKernel`](@ref) は、$\alpha \to \infty$ の極限で回復されます。

関連情報: [`GammaRationalKernel`](@ref)
