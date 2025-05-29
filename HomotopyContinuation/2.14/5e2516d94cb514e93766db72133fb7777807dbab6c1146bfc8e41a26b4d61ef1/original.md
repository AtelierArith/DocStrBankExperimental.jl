```
CoefficientHomotopy(
    F::Union{AbstractSystem,System};
    start_coefficients,
    target_coefficients,
)
```

Construct the homotopy $H(x, t) = ∑_{a ∈ Aᵢ} (c_a t + (1-t)d_a) x^a$ where $c_a$ are the start coefficients and $d_a$ the target coefficients.
