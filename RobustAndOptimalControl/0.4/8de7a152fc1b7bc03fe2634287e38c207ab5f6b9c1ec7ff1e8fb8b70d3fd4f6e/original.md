```
add_input_integrator(sys::StateSpace, ui = 1, ϵ = 0)
```

Augment the output of `sys` with the integral of input at index `ui`, i.e.,  `y_aug = [y; ∫u[ui]]` See also [`add_low_frequency_disturbance`](@ref)
