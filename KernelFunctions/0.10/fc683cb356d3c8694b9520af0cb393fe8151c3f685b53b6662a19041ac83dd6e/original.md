```
ExponentialKernel(; metric=Euclidean())
```

Exponential kernel with respect to the `metric`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the exponential kernel is defined as

$$
k(x, x') = \exp\big(- d(x, x')\big).
$$

By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

See also: [`GammaExponentialKernel`](@ref)
