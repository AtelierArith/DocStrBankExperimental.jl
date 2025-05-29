```
product_peps(peps_args...; unitcell=(1, 1), noise_amp=1e-2, state_vector=nothing)
```

Initialize a normalized random product PEPS with noise. The given arguments are passed on to the `InfinitePEPS` constructor.

The noise intensity can be tuned with `noise_amp`. The product state coefficients can be specified using the `state_vector` kwarg in the form of a matrix of size `unitcell` containing vectors that match the PEPS physical dimensions. If `nothing` is provided, random Gaussian coefficients are used.
