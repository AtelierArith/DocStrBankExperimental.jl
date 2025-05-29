```
add_output_integrator(sys::StateSpace{<:Discrete}, ind = 1; ϵ = 0)
```

Augment the output of `sys` with the integral of output at index `ind`, i.e.,  `y_aug = [y; ∫y[ind]]` To add both an integrator and a differentiator to a SISO system, use

```julia
Gd = add_output_integrator(add_output_differentiator(G), 1)
```

Note: numerical integration is subject to numerical drift. If the output of the system corresponds to, e.g., a velocity reference and the integral to position reference, consider methods for mitigating this drift.
