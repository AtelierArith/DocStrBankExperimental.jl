```
dlegendre!(dP::AbstractMatrix, ϕ::Number, P::AbstractMatrix, n_max::Integer = -1, m_max::Integer = -1; kwargs...) -> Nothing
```

Compute the first-order derivative of the associated Legendre function `P_n,m[cos(ϕ)]` with respect to `ϕ` [rad]:

```
∂P_n,m[cos(ϕ)]
──────────────
     ∂ϕ
```

The maximum degree and order that will be computed are given by the parameters `n_max` and `m_max`. If they are negative (default), the dimensions of matrix `dP` will be used:

```
maximum degree -> number of rows - 1
maximum order  -> number of columns - 1
```

The derivatives will be stored in the matrix `dP`.

The parameter `N` selects the normalization. The following values are valid:

  * `Val(:full)`: Compute the fully normalized associated Legendre function.
  * `Val(:schmidt)`: Compute the Schmidt quasi-normalized associated Legendre function.
  * `Val(:unnormalized)`: Compute the unnormalized associated Legendre function.

This algorithm needs the matrix `P` with the values of the associated Legendre function using the same normalization `N`, which can be computed using the function [`legendre`](@ref).

!!! warning
    The user is responsible to pass a matrix `P` with the correct values. For example, if `ph_term` is `true`, `P` must also be computed with `ph_term` set to `true`.


# Keywords

  * `ph_term::Bool`: If `true`, the Condon-Shortley phase term `(-1)^m` will be included.   (**Default** = `false`)
