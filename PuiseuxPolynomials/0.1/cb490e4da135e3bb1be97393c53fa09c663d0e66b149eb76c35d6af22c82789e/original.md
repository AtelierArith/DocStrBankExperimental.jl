`laurent_denominator(p1,p2,…)`

returns  the unique  monomial `m`  of minimal  degree in each variable such that  for all  the Laurent  polynomials `p1,p2,…`  the product `m*pᵢ` has a positive degree in each variable.

```julia-repl
julia> laurent_denominator(x^-1,y^-2+x^4)
Monomial{Int64}:xy²
```
