```julia
check_pure_state(ρ; atol, rtol)

```

Check whether the input `ρ` is a pure state: $tr(ρ²)≈1$. This function will first check if `ρ` is a valid density matrix. `atol` and `rtol` are the corresponding absolute and relative error tolerance used for float point number comparison. The default values are `atol = 0` and `rtol = atol>0 ? 0 : √eps`.
