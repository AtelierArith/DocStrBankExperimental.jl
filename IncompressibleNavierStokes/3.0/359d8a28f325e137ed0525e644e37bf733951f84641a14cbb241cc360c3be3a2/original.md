```julia
stretched_grid(a, b, N) -> Any
stretched_grid(a, b, N, s) -> Any

```

Create a nonuniform grid of `N + 1` points from `a` to `b` with a stretch factor of `s`. If `s = 1`, return a uniform spacing from `a` to `b`. Otherwise, return a vector $x \in \mathbb{R}^{N + 1}$ such that $x_n = a + \sum_{i = 1}^n s^{i - 1} h$ for $n = 0, \dots , N$. Setting $x_N = b$ then gives $h = (b - a) \frac{1 - s}{1 - s^N}$, resulting in

$$
x_n = a + (b - a) \frac{1 - s^n}{1 - s^N}, \quad n = 0, \dots, N.
$$

Note that `stretched_grid(a, b, N, s)[n]` corresponds to $x_{n - 1}$.

See also [`cosine_grid`](@ref).
