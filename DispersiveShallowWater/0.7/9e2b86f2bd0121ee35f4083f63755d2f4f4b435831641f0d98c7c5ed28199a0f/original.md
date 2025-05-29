```
LinearDispersionRelation(ref_height)
```

A struct representing a linear dispersion relation $\omega(k)$ of an equation. The reference water height $h_0$ is given by `ref_height`. A dispersion relation can be called as `disp_rel(equations, k)` to compute the wave frequency $\omega(k)$ for a given wavenumber `k` and a set of equations.

See also [`wave_speed`](@ref) for computing the wave speed $c = \omega(k) / k$ given a linear dispersion relation.
