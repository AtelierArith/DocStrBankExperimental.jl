```
`armijo(h::Any, h_at_t::OneDAtX{S, T}; τ₀::T = T(0.01), kwargs...) where {S, T}`
```

Check if a step size is admissible according to the Armijo criterion.

Armijo criterion: `f(x + θd) - f(x) - τ₀ θ ∇f(x+θd)d < 0`

This function returns the maximum between the left-hand side and 0.

Note: `fx`, `f₀` and `g₀` are required in the `OneDAtX`.

See also `wolfe`, `armijo_wolfe`, `shamanskii_stop`, `goldstein`
