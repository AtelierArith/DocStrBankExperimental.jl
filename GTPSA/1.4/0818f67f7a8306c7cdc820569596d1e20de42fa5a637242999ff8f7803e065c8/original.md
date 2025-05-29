```
cycle!(t::TPS, i, n, m_, v_)
```

Given a starting index `i` (-1 if starting at 0), will optionally fill monomial `m_` (if `m != C_NULL`, and `m_` is a `DenseVector{UInt8}`) with the monomial at index `i`  and optionally the value at `v_` with the monomials coefficient (if `v_ != C_NULL`,  and `v_` is a `Ref{<:Union{Float64,ComplexF64}}`), and return the next NONZERO monomial  index in the `TPS`. This is useful for iterating through each monomial in the TPSA.

### Input

  * `t`  – TPS to scan
  * `i`  – Index to start from (-1 to start at 0)
  * `n`  – Length of monomial
  * `m_` – (Optional) Monomial to be filled if provided
  * `v_` – (Optional) Pointer to value of coefficient

### Output

  * `i`  – Index of next nonzero monomial in the TPSA, or -1 if reached the end
