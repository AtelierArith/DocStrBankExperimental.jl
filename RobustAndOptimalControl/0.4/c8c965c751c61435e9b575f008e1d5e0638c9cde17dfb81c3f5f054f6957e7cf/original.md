```
add_differentiator(sys::StateSpace{<:Discrete})
```

Augment the output of `sys` with the numerical difference (discrete-time derivative) of output, i.e., `y_aug = [y; (y-y_prev)/sys.Ts]` To add both an integrator and a differentiator to a SISO system, use

```julia
Gd = add_output_integrator(add_output_differentiator(G), 1)
```
