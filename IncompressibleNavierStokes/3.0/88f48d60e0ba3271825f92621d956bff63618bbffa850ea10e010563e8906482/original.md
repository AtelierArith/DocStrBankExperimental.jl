```julia
kinetic_energy(u, setup; kwargs...) -> Any

```

Compute kinetic energy field $k$ (in-place version). If `interpolate_first` is true, it is given by

$$
k_I = \frac{1}{8} \sum_\alpha (u^\alpha_{I + h_\alpha} + u^\alpha_{I - h_\alpha})^2.
$$

Otherwise, it is given by

$$
k_I = \frac{1}{4} \sum_\alpha ((u^\alpha_{I + h_\alpha})^2 + (u^\alpha_{I - h_\alpha})^2),
$$

as in [Sanderse2023](@cite).

Differentiable version.
