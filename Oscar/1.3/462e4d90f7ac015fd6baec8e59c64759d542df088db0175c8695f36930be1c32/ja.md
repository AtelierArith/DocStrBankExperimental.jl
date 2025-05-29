```
is_zero(m::SubquoModuleElem)
```

`m` がゼロの場合は `true` を返し、それ以外の場合は `false` を返します。

# 例

```jldoctest
julia> R, (x, y, z) = polynomial_ring(QQ, [:x, :y, :z])
(Multivariate polynomial ring in 3 variables over QQ, QQMPolyRingElem[x, y, z])

julia> F = free_module(R, 1)
Free module of rank 1 over R

julia> A = R[x; y]
[x]
[y]

julia> B = R[x^2; y^3; z^4]
[x^2]
[y^3]
[z^4]

julia> M = SubquoModule(F, A, B)
Subquotient of submodule with 2 generators
  1: x*e[1]
  2: y*e[1]
by submodule with 3 generators
  1: x^2*e[1]
  2: y^3*e[1]
  3: z^4*e[1]

julia> is_zero(M[1])
false

julia> is_zero(x*M[1])
true
```

```jldoctest
julia> Rg, (x, y, z) = graded_polynomial_ring(QQ, [:x, :y, :z]);

julia> F = graded_free_module(Rg, 1)
Graded free module Rg^1([0]) of rank 1 over Rg

julia> A = Rg[x; y]
[x]
[y]

julia> B = Rg[x^2; y^3; z^4]
[x^2]
[y^3]
[z^4]

julia> M = SubquoModule(F, A, B)
Graded subquotient of graded submodule of F with 2 generators
  1: x*e[1]
  2: y*e[1]
by graded submodule of F with 3 generators
  1: x^2*e[1]
  2: y^3*e[1]
  3: z^4*e[1]

julia> is_zero(M[1])
false

julia> is_zero(x*M[1])
true

```
