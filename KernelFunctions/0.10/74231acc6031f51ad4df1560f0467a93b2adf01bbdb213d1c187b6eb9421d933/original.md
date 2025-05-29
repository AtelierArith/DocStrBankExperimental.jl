```
LinearKernel(; c::Real=0.0)
```

Linear kernel with constant offset `c`.

# Definition

For inputs $x, x' \in \mathbb{R}^d$, the linear kernel with constant offset $c \geq 0$ is defined as

$$
k(x, x'; c) = x^\top x' + c.
$$

See also: [`PolynomialKernel`](@ref)
