```
Matern52Kernel(; metric=Euclidean())
```

Matérn kernel of order $5/2$ with respect to the `metric`.

# Definition

For inputs $x, x'$ and metric $d(\cdot, \cdot)$, the Matérn kernel of order $5/2$ is given by

$$
k(x, x') = \bigg(1 + \sqrt{5} d(x, x') + \frac{5}{3} d(x, x')^2\bigg)
           \exp\big(- \sqrt{5} d(x, x') \big).
$$

By default, $d$ is the Euclidean metric $d(x, x') = \|x - x'\|_2$.

See also: [`MaternKernel`](@ref)
