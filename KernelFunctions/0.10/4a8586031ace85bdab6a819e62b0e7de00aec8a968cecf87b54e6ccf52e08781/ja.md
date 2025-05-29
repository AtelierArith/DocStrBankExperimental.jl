```
GammaRationalKernel(; α::Real=2.0, γ::Real=1.0, metric=Euclidean())
```

γ-有理カーネルは、形状パラメータ `α` と `γ` に対して `metric` に関して定義されます。

# 定義

入力 $x, x'$ と距離 $d(\cdot, \cdot)$ に対して、形状パラメータ $\alpha > 0$ および $\gamma \in (0, 2]$ の γ-有理カーネルは次のように定義されます。

$$
k(x, x'; \alpha, \gamma) = \bigg(1 + \frac{d(x, x')^{\gamma}}{\alpha}\bigg)^{-\alpha}.
$$

デフォルトでは、$d$ はユークリッド距離 $d(x, x') = \|x - x'\|_2$ です。

[`GammaExponentialKernel`](@ref) は、$\alpha \to \infty$ の極限で回復されます。

関連情報: [`RationalKernel`](@ref), [`RationalQuadraticKernel`](@ref)
