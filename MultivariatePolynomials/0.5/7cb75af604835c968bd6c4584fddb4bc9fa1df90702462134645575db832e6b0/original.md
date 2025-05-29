```
degree_complex(t::AbstractTermLike)
```

Return the *total complex degree* of the monomial of the term `t`, i.e., the maximum of the total degree of the declared variables in `t` and the total degree of the conjugate variables in `t`. To be well-defined, the monomial must not contain real parts or imaginary parts of variables. If `x₁` and `x₂` are real-valued variables and `z₁` and `z₂` are complex-valued,

  * `degree_complex(x₁^2 * x₂^3) = 5`
  * `degree_complex(z₁^3 * conj(z₁)^4) = max(3, 4) = 4` and `degree_complex(z₁^4 * conj(z₁)^3) = max(4, 3) = 4`
  * `degree_complex(z₁^3 * z₂ * conj(z₁)^2 * conj(z₂)^4) = max(4, 6) = 6` and `degree_complex(z₁^4 * z₂ * conj(z₁) * conj(z₂)^3) = max(5, 4) = 5`
  * `degree_complex(x₁^2 * x₂^3 * z₁^3 * z₂ * conj(z₁)^2 * conj(z₂)^4) = 5 + max(4, 6) = 11`
