```
collectPlm(x; m::Integer, lmax::Integer, [lmin::Integer = abs(m)], [kwargs...])
```

Compute the associated Legendre polynomials $P_\ell^m(x)$ for the argument `x`, degrees `l = lmin:lmax` and order `m` lying in `-l:l`.

Returns `v` with indices `lmin:lmax`, with `v[l] == Plm(x, l, m; kwargs...)`.

# Optional keyword arguments

  * `norm`: The normalization used in the function. Possible   options are `Val(:standard)` (default), `Val(:normalized)`, `Val(:schmidtquasi)` or `Val(:schmidt)`.

      * The functions obtained with `norm = Val(:normalized)` have an L2 norm of $1$.
      * The functions obtained with `norm = Val(:schmidtquasi)` have an L2 norm of $\sqrt{\frac{2(2-\delta_{m0})}{2l+1}}$.
      * The functions obtained with `norm = Val(:schmidt)` have an L2 norm of $\sqrt{2(2-\delta_{m0})}$.
  * `csphase::Bool`: The Condon-shortley phase $(-1)^m$, which is included by default.
  * `Tnorm`: Type of the normalization factor, which is dynamicall inferred by default,   and is used in allocating an appropriate container.   In case it is known that the norm may be expressed as a certain type without overflow   (eg. `Float64`), this may be provided. Care must be taken to avoid overflows if `Tnorm`   is passed as an argument.

# Examples

```jldoctest
julia> v = collectPlm(0.5, lmax = 3, m = 2);

julia> all(l -> v[l] ≈ Plm(0.5, l, 2), 2:3)
true

julia> v = collectPlm(0.5, lmax = 3, m = 2, norm = Val(:normalized));

julia> all(l -> v[l] ≈ Plm(0.5, l, 2, norm = Val(:normalized)), 2:3)
true
```
