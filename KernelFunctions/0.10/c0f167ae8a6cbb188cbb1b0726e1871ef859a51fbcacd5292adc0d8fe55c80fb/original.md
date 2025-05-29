```
RationalQuadraticKernel(; α::Real=2.0, metric=Euclidean())
```

Rational-quadratic kernel with respect to the `metric` and with shape parameter `α`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the rational-quadratic kernel with shape parameter $\alpha > 0$ is defined as

$$
k(x, x'; \alpha) = \bigg(1 + \frac{d(x, x')^2}{2\alpha}\bigg)^{-\alpha}.
$$

By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

The [`SqExponentialKernel`](@ref) is recovered in the limit as $\alpha \to \infty$.

See also: [`GammaRationalKernel`](@ref)
