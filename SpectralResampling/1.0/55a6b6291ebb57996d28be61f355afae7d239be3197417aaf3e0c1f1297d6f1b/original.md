```
get_linear_λ(lnλ[, lin_spacing])
```

Does the opposite of `get_logarithmic_λ`, returning a linearly spaced wavelength vector given a logarithmically spaced one. Optionally specify the spacing in linear space with the `lin_spacing` argument, defined such that `lin_spacing = λ[2] - λ[1] = λ[end] - λ[end-1]`.
