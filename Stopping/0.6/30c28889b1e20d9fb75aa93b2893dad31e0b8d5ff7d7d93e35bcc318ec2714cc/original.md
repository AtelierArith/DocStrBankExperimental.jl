```
`armijo_wolfe(h::Any, h_at_t::OneDAtX{S, T}; τ₀::T = T(0.01), τ₁::T = T(0.99), kwargs...) where {S, T}`
```

Check if a step size is admissible according to the Armijo and Wolfe criteria.

Note: `fx`, `f₀`, `gx` and `g₀` are required in the `OneDAtX`.

See also `armijo`, `wolfe`, `shamanskii_stop`, `goldstein`
