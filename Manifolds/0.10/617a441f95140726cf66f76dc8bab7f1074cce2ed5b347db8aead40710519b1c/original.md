```
exp(M::Circle, p, X)
```

Compute the exponential map on the [`Circle`](@ref).

$$
\exp_p X = (p+X)_{2π},
$$

where $(⋅)_{2π}$ is the (symmetric) remainder with respect to division by $2π$, i.e. in $[-π,π)$.

For the complex-valued case, the same formula as for the [`Sphere`](@ref) $𝕊^1$ is applied to values in the complex plane.
