```
NegativeDomain(; metaprogramming::Bool = true, μ::Real = 1, ϵ::Real = eps(), low::Real = -1e10, high::Real = 1e10, tol::Real = 1e-10, maxiter::Real = 1e6)
```

Returns an instance of `Options` configured for optimization over the negative domain. Sets defaults for `A` and `V` parameters while keeping the remaining settings from `Options`.

# Specific Settings

  * `A_init_value = -1`: Initializes `A` with a negative value.
  * `A_upper = -1e-4`: Upper bound for `A` is constrained to a small negative value.
  * `V_init_value = 1`: Initializes `V` with a positive value.
  * `V_lower = 1e-4`: Lower bound for `V` is constrained to a small positive value.

Other fields inherit from the `Options` struct.
