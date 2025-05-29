```
rand(M::Segre{ℝ, V}; vector_at=nothing)
```

If `vector_at` is `nothing`, return a random point on

$$
    ℝ^{+} × \mathbb{S}^{n_1 - 1} ×⋯× \mathbb{S}^{n_d - 1}
$$

from a log-normal distribution on $ℝ^{+}$ and a uniform distribution on $\mathbb{S}^{n_1 - 1} ×⋯× \mathbb{S}^{n_d - 1}$.

If `vector_at` is not `nothing`, return a random tangent vector from a normal distribution on the tangent space.
