# Extended help

```
ρ(d::AbstractVector, B::BallInf)
```

### Algorithm

Let $B$ be a ball in the infinity norm with center $c$ and radius $r$ and let $d$ be the direction of interest. For balls with dimensions less than $30$, we use the implementation for `AbstractHyperrectangle`, tailored to a `BallInf`, which computes

$$
    ∑_{i=1}^n d_i (c_i + \textrm{sgn}(d_i) · r)
$$

where $\textrm{sgn}(α) = 1$ if $α ≥ 0$ and $\textrm{sgn}(α) = -1$ if $α < 0$.

For balls of higher dimension, we instead exploit that for a support vector $v = σ(d, B) = c + \textrm{sgn}(d) · (r, …, r)ᵀ$ we have

$$
    ρ(d, B) = ⟨d, v⟩ = ⟨d, c⟩ + ⟨d, \textrm{sgn}(d) · (r, …, r)ᵀ⟩ = ⟨d, c⟩ + r · ∑_{i=1}^n |d_i|
$$

where $⟨·, ·⟩$ denotes the dot product.
