```
GammaExponentialKernel(; γ::Real=1.0, metric=Euclidean())
```

γ-exponential kernel with respect to the `metric` and with parameter `γ`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the γ-exponential kernel[^RW] with parameter $\gamma \in (0, 2]$ is defined as

$$
k(x, x'; \gamma) = \exp\big(- d(x, x')^{\gamma}\big).
$$

By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

See also: [`ExponentialKernel`](@ref), [`SqExponentialKernel`](@ref)

[^RW]: C. E. Rasmussen & C. K. I. Williams (2006). Gaussian Processes for Machine Learning.
