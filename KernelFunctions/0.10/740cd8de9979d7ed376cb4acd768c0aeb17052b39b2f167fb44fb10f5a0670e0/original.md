```
SqExponentialKernel(; metric=Euclidean())
```

Squared exponential kernel with respect to the `metric`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the squared exponential kernel is defined as

$$
k(x, x') = \exp\bigg(- \frac{d(x, x')^2}{2}\bigg).
$$

By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

See also: [`GammaExponentialKernel`](@ref)
