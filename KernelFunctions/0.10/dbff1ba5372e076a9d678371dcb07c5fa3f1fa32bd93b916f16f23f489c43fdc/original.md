```
PolynomialKernel(; degree::Int=2, c::Real=0.0)
```

Polynomial kernel of degree `degree` with constant offset `c`.

# Definition

For inputs $x, x' \in \mathbb{R}^d$, the polynomial kernel of degree $\nu \in \mathbb{N}$ with constant offset $c \geq 0$ is defined as

$$
k(x, x'; c, \nu) = (x^\top x' + c)^\nu.
$$

See also: [`LinearKernel`](@ref)
