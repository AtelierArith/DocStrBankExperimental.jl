```
TorQuadModuleMap
```

Type for abelian group homomorphisms between torsion quadratic modules. It consists of a header which keeps track of the domain and the codomain of type `TorQuadModule` as well as the underlying abelian group homomorphism.

# Examples

```jldoctest
julia> L = rescale(root_lattice(:A,3), 3)
Integer lattice of rank 3 and degree 3
with gram matrix
[ 6   -3    0]
[-3    6   -3]
[ 0   -3    6]

julia> T = discriminant_group(L)
Finite quadratic module
  over integer ring
Abelian group: (Z/3)^2 x Z/12
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[2//3      0   1//3]
[   0      0   2//3]
[1//3   2//3   1//4]

julia> N, f = normal_form(T)
(Finite quadratic module: (Z/3)^2 x Z/12 -> Q/2Z, Map: finite quadratic module -> finite quadratic module)


julia> domain(f)
Finite quadratic module
  over integer ring
Abelian group: (Z/3)^2 x Z/12
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[2//3      0   1//3]
[   0      0   2//3]
[1//3   2//3   1//4]

julia> codomain(f)
Finite quadratic module
  over integer ring
Abelian group: (Z/3)^2 x Z/12
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[1//4      0      0      0]
[   0   4//3      0      0]
[   0      0   4//3      0]
[   0      0      0   4//3]

julia> abelian_group_homomorphism(f)
Map
  from (Z/3)^2 x Z/12
  to finitely generated abelian group with 4 generators and 4 relations
```

Note that an object of type `TorQuadModuleMap` needs not to be a morphism of torsion quadratic modules, i.e. it does not have to preserve the respective bilinear or quadratic forms of its domain and codomain. Though, it must be a homomorphism between the underlying finite abelian groups.

# Examples

```jldoctest
julia> L = rescale(root_lattice(:A,3), 3);

julia> T = discriminant_group(L)
Finite quadratic module
  over integer ring
Abelian group: (Z/3)^2 x Z/12
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[2//3      0   1//3]
[   0      0   2//3]
[1//3   2//3   1//4]

julia> T6 = rescale(T, 6)
Finite quadratic module
  over integer ring
Abelian group: (Z/3)^2 x Z/12
Bilinear value module: Q/6Z
Quadratic value module: Q/12Z
Gram matrix quadratic form:
[4   0      2]
[0   0      4]
[2   4   3//2]

julia> f = hom(T, T6, gens(T6))
Map
  from finite quadratic module: (Z/3)^2 x Z/12 -> Q/2Z
  to finite quadratic module: (Z/3)^2 x Z/12 -> Q/12Z

julia> T[1]*T[1] == f(T[1])*f(T[1])
false

julia> is_bijective(f)
true
```

Hecke provides several constructors for objects of type `TorQuadModuleMap`, see for instance [`hom(::TorQuadModule, ::TorQuadModule, ::ZZMatrix)`](@ref), [`hom(::TorQuadModule, ::TorQuadModule, ::Vector{TorQuadModuleElem})`](@ref), [`identity_map(::TorQuadModule)`](@ref) or [`trivial_morphism(::TorQuadModule)`](@ref).
