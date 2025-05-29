```
wave_speed(disp_rel, equations, k; normalize = false)
```

Compute the wave speed $c$ for a given wavenumber $k$ using the [`LinearDispersionRelation`](@ref) `disp_rel` of the `equations`. The wave speed is given by $c = \omega(k) / k$. If `normalize` is `true`, the wave speed is normalized by the shallow water wave speed $\sqrt{g h_0}$, where $g$ is the gravitational acceleration of the `equations` and $h_0$ is the `ref_height` of the dispersion relation `disp_rel`.

See also [`LinearDispersionRelation`](@ref).
