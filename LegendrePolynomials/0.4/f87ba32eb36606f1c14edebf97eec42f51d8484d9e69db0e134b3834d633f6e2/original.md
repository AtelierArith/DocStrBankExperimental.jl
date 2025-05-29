```
Plm(x, l::Integer, m::Integer; [kwargs...])
```

Compute the associated Legendre polynomial $P_\ell^m(x)$ for degree `l` and order $m$ lying in `-l:l`.

For `m == 0` this function returns Legendre polynomials.

# Optional keyword arguments

  * `norm`: The normalization used in the function. Possible   options are `Val(:standard)` (default), `Val(:normalized)`, `Val(:schmidtquasi)` or `Val(:schmidt)`.

      * The functions obtained with `norm = Val(:normalized)` have an L2 norm of $1$.
      * The functions obtained with `norm = Val(:schmidtquasi)` have an L2 norm of $\sqrt{\frac{2(2-\delta_{m0})}{2l+1}}$.
      * The functions obtained with `norm = Val(:schmidt)` have an L2 norm of $\sqrt{2(2-\delta_{m0})}$.
  * `csphase::Bool`: The Condon-shortley phase $(-1)^m$, which is included by default.

# Examples

```jldoctest
julia> Plm(0.5, 3, 2) ≈ 45/8 # analytically obtained value
true

julia> Plm(0.5, 4, 0) == Pl(0.5, 4)
true
```
