```
GammaRationalKernel(; α::Real=2.0, γ::Real=1.0, metric=Euclidean())
```

γ-rational kernel with respect to the `metric` with shape parameters `α` and `γ`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the γ-rational kernel with shape parameters $\alpha > 0$ and $\gamma \in (0, 2]$ is defined as

$$
k(x, x'; \alpha, \gamma) = \bigg(1 + \frac{d(x, x')^{\gamma}}{\alpha}\bigg)^{-\alpha}.
$$

By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

The [`GammaExponentialKernel`](@ref) is recovered in the limit as $\alpha \to \infty$.

See also: [`RationalKernel`](@ref), [`RationalQuadraticKernel`](@ref)
