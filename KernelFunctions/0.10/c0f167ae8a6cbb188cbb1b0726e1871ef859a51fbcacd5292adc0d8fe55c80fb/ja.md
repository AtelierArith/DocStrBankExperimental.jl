```
RationalQuadraticKernel(; α::Real=2.0, metric=Euclidean())
```

メトリックに関するラショナル二次カーネルと形状パラメータ `α`。

# 定義

入力 $x, x'$ とメトリック $d(\cdot, \cdot)$ に対して、形状パラメータ $\alpha > 0$ のラショナル二次カーネルは次のように定義されます。

$$
k(x, x'; \alpha) = \bigg(1 + \frac{d(x, x')^2}{2\alpha}\bigg)^{-\alpha}.
$$

デフォルトでは、$d$ はユークリッドメトリック $d(x, x') = \|x - x'\|_2$ です。

[`SqExponentialKernel`](@ref) は、$\alpha \to \infty$ の極限で回復されます。

関連情報: [`GammaRationalKernel`](@ref)
