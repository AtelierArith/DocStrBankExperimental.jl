```
`wolfe(h::Any, h_at_t::OneDAtX{S, T}; τ₁::T = T(0.99), kwargs...) where {S, T}`
```

Check if a step size is admissible according to the Wolfe criterion.

Strong Wolfe criterion: `|∇f(x+θd)| - τ₁||∇f(x)|| < 0`.

This function returns the maximum between the left-hand side and 0.

Note: `gx` and `g₀` are required in the `OneDAtX`.

See also `armijo`, `armijo_wolfe`, `shamanskii_stop`, `goldstein`
