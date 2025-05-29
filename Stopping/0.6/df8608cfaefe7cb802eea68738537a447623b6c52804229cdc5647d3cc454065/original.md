```
`goldstein(h::Any, h_at_t::OneDAtX{S, T}; τ₀::T = T(0.0001), τ₁::T = T(0.9999), kwargs...) where {S, T}`
```

Check if a step size is admissible according to the Goldstein criteria.

Note: `fx`, `f₀` and `g₀` are required in the `OneDAtX`.

See also `armijo`, `wolfe`, `armijo_wolfe`, `shamanskii_stop`
