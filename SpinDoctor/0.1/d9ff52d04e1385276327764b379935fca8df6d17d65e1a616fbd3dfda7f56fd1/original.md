```
int_F²(f)
```

Compute the time profile contribution to the $b$-value given the time profile `f`. The $b$-value is given by

```julia
b = γ^2 * g^2 * int_F²(f)
```

where `γ` is the gyromagnetic ratio of the water proton and `g` is the gradient amplitude.
