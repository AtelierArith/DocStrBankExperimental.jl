```
RationalKernel(; α::Real=2.0, metric=Euclidean())
```

Rational kernel with shape parameter `α` and given `metric`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the rational kernel with shape parameter $\alpha > 0$ is defined as

$$
k(x, x'; \alpha) = \bigg(1 + \frac{d(x, x')}{\alpha}\bigg)^{-\alpha}.
$$

By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

The [`ExponentialKernel`](@ref) is recovered in the limit as $\alpha \to \infty$.

See also: [`GammaRationalKernel`](@ref)
