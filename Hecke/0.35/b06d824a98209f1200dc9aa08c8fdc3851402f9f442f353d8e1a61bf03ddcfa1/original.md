```
torsion_quadratic_module(q::QQMatrix) -> TorQuadModule
```

Return a torsion quadratic module with gram matrix given by `q` and value module `Q/Z`. If all the diagonal entries of `q` have: either even numerator or even denominator, then the value module of the quadratic form is `Q/2Z`

# Example

```jldoctest
julia> torsion_quadratic_module(QQ[1//6;])
Finite quadratic module
  over integer ring
Abelian group: Z/6
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[1//6]

julia> torsion_quadratic_module(QQ[1//2;])
Finite quadratic module
  over integer ring
Abelian group: Z/2
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[1//2]

julia> torsion_quadratic_module(QQ[3//2;])
Finite quadratic module
  over integer ring
Abelian group: Z/2
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[3//2]

julia> torsion_quadratic_module(QQ[1//3;])
Finite quadratic module
  over integer ring
Abelian group: Z/3
Bilinear value module: Q/Z
Quadratic value module: Q/Z
Gram matrix quadratic form:
[1//3]
```
