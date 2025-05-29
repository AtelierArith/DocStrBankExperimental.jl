```
growth_witness(shift::AbstractArray, norm::AbstractArray, dt, [b]; skip=0)
```

Compute the growth witness

$$
G^{(n)} = S^{(n)} - \frac{\vert\mathbf{c}^{(n+1)}\vert -
          \vert\mathbf{c}^{(n)}\vert}{\vert\mathbf{c}^{(n)}\vert d\tau},
$$

where `S` is the `shift` and $\vert\mathbf{c}^{(n)}\vert ==$ `norm[n, 1]`. Setting `b ≥ 1` a sliding average over `b` time steps is computed using [`smoothen()`](@ref). The first `skip` time steps are skipped. `mean(growth_witness)` is approximately the same as [`growth_estimator`](@ref) with `h=0`.

See also [`growth_estimator`](@ref).
