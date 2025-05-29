```
is_subset(M::SubquoModule{T}, N::SubquoModule{T}) where T
```

Given subquotients `M` and `N` such that `ambient_module(M) == ambient_module(N)`, return `true` if `M` is contained in `N`, where `M` and `N` are regarded as submodules  of the common ambient module.

# Examples

```jldoctest
julia> R, (x, y, z) = polynomial_ring(QQ, [:x, :y, :z])
(Multivariate polynomial ring in 3 variables over QQ, QQMPolyRingElem[x, y, z])

julia> F = free_module(R, 1)
Free module of rank 1 over R

julia> AM = R[x;]
[x]

julia> BM = R[x^2; y^3; z^4]
[x^2]
[y^3]
[z^4]

julia> M = SubquoModule(F, AM, BM)
Subquotient of submodule with 1 generator
  1: x*e[1]
by submodule with 3 generators
  1: x^2*e[1]
  2: y^3*e[1]
  3: z^4*e[1]

julia> AN = R[x; y]
[x]
[y]

julia> BN = R[x^2+y^4; y^3; z^4]
[x^2 + y^4]
[      y^3]
[      z^4]

julia> N = SubquoModule(F, AN, BN)
Subquotient of submodule with 2 generators
  1: x*e[1]
  2: y*e[1]
by submodule with 3 generators
  1: (x^2 + y^4)*e[1]
  2: y^3*e[1]
  3: z^4*e[1]

julia> is_subset(M, N)
true
```

```jldoctest
julia> Rg, (x, y, z) = graded_polynomial_ring(QQ, [:x, :y, :z]);

julia> F = graded_free_module(Rg, 2);

julia> O1 = [x*F[1]+y*F[2],y*F[2]];

julia> O1a = [x*F[1],y*F[2]];

julia> O2 = [x^2*F[1]+y^2*F[2],y^2*F[2]];

julia> M1 = SubquoModule(F, O1, O2)
Graded subquotient of graded submodule of F with 2 generators
  1: x*e[1] + y*e[2]
  2: y*e[2]
by graded submodule of F with 2 generators
  1: x^2*e[1] + y^2*e[2]
  2: y^2*e[2]

julia> M2 = SubquoModule(F, O1a, O2)
Graded subquotient of graded submodule of F with 2 generators
  1: x*e[1]
  2: y*e[2]
by graded submodule of F with 2 generators
  1: x^2*e[1] + y^2*e[2]
  2: y^2*e[2]

julia> is_subset(M1,M2)
true

julia> is_subset(M2,M1)
true

julia> M1 == M2
true
```
