```
collectPlm!(v::AbstractVector, x; m::Integer, [lmin::Integer = abs(m)], [lmax::Integer = length(v) - 1 + lmin], [kwargs...])
```

Compute the associated Legendre polynomials $P_\ell^m(x)$ for the argument `x`, degrees `l = lmin:lmax` and order `m` lying in `-l:l`, and store the result in `v`.

At output, `v[l + firstindex(v)] == Plm(x, l, m; kwargs...)` for `l = lmin:lmax`.

# Optional keyword arguments

  * `norm`: The normalization used in the function. Possible   options are `Val(:standard)` (default), `Val(:normalized)`, `Val(:schmidtquasi)` or `Val(:schmidt)`.

      * The functions obtained with `norm = Val(:normalized)` have an L2 norm of $1$.
      * The functions obtained with `norm = Val(:schmidtquasi)` have an L2 norm of $\sqrt{\frac{2(2-\delta_{m0})}{2l+1}}$.
      * The functions obtained with `norm = Val(:schmidt)` have an L2 norm of $\sqrt{2(2-\delta_{m0})}$.
  * `csphase::Bool`: The Condon-shortley phase $(-1)^m$, which is included by default.

# Examples

```jldoctest
julia> v = zeros(2);

julia> collectPlm!(v, 0.5, lmax = 3, m = 2);

julia> all(zip(2:3, v)) do (l, vl); vl ≈ Plm(0.5, l, 2); end
true
```
