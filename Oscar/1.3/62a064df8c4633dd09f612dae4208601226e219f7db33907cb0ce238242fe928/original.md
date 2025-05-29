```
is_zero(M::SubquoModule)
```

Return `true` if `M` is the zero module, `false` otherwise.

# Examples

```jldoctest
julia> R, (x, y, z) = polynomial_ring(QQ, [:x, :y, :z])
(Multivariate polynomial ring in 3 variables over QQ, QQMPolyRingElem[x, y, z])

julia> F = free_module(R, 1)
Free module of rank 1 over R

julia> A = R[x^2+y^2;]
[x^2 + y^2]

julia> B = R[x^2; y^3; z^4]
[x^2]
[y^3]
[z^4]

julia> M = SubquoModule(F, A, B)
Subquotient of submodule with 1 generator
  1: (x^2 + y^2)*e[1]
by submodule with 3 generators
  1: x^2*e[1]
  2: y^3*e[1]
  3: z^4*e[1]

julia> is_zero(M)
false
```
