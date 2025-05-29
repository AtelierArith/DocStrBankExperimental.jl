```
log(M::Circle, p, q)
```

Compute the logarithmic map on the [`Circle`](@ref) `M`.

$$
\log_p q = (q-p)_{2π},
$$

where $(⋅)_{2π}$ is the (symmetric) remainder with respect to division by $2π$, i.e. in $[-π,π)$.

For the complex-valued case, the same formula as for the [`Sphere`](@ref) $𝕊^1$ is applied to values in the complex plane.
