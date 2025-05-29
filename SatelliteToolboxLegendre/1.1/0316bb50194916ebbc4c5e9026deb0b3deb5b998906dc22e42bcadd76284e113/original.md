```
dlegendre(N, ϕ::T, n_max::Integer, m_max::Integer = -1; kwargs...) where T<:Number -> Matrix{float(T)}, Matrix{float(T)}
```

Compute the first-order derivative of the associated Legendre function `P_n,m[cos(ϕ)]` with respect to `ϕ` [rad]:

```
∂P_n,m[cos(ϕ)]
──────────────
     ∂ϕ
```

The maximum degree that will be computed is `n_max` and the maximum order is `m_max`. Notice that if `m_max` is higher than `n_max` or negative (default), it is set to `n_max`.

The parameter `N` selects the normalization. The following values are valid:

  * `Val(:full)`: Compute the fully normalized associated Legendre function.
  * `Val(:schmidt)`: Compute the Schmidt quasi-normalized associated Legendre function.
  * `Val(:unnormalized)`: Compute the unnormalized associated Legendre function.

# Keywords

  * `ph_term::Bool`: If `true`, the Condon-Shortley phase term `(-1)^m` will be included.   (**Default** = `false`)

# Returns

  * `Matrix{float(T)}`: A matrix with the first-order derivative of the Legendre associated   functions `P_n,m[cos(ϕ)]`.
  * `Matrix{float(T)}`: A matrix with the Legendre associated functions `P_n,m[cos(ϕ)]`.
