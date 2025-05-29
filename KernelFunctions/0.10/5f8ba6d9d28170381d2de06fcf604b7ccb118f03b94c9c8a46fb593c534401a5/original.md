```
Matern32Kernel(; metric=Euclidean())
```

Matérn kernel of order $3/2$ with respect to the `metric`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the Matérn kernel of order $3/2$ is  given by

$$
k(x, x') = \big(1 + \sqrt{3} d(x, x') \big) \exp\big(- \sqrt{3} d(x, x') \big).
$$

By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

See also: [`MaternKernel`](@ref)
