```
subgrad_distance(M, q, p[, c = 2; atol = 0])
subgrad_distance!(M, X, q, p[, c = 2; atol = 0])
```

compute the subgradient of the distance (in place of `X`)

$$
f(p) = \frac{1}{c} d^c_{\mathcal M}(p, q)
$$

to a fixed point `q` on the manifold `M` and `c` is an integer. The subgradient reads

$$
\partial f(p) = -d_{\mathcal M}^{c-2}(p, q)\log_pq
$$

for $c\neq 1$ or $p\neq  q$. Note that for the remaining case $c=1$, $p=q$, the function is not differentiable. In this case, the subgradient is given by a tangent vector at `p` with norm less than or equal to one.

# Optional

  * `c` – (`2`) the exponent of the distance,  i.e. the default is the distance
  * `atol` – (`0`) the tolerance to use when evaluating the distance between `p` and `q`.
