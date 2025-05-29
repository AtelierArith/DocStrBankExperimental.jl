```
truncatemincoeff(coeff, min_abs_coeff::Real)
```

Return `true` if `abs(coeff) < min_abs_coeff`. Truncations on coefficients should default to false if it is not applicable for a type.
