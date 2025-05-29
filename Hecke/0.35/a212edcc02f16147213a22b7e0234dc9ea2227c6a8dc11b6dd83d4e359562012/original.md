```
is_isometric_with_isometry(T::TorQuadModule, U::TorQuadModule)
                                               -> Bool, TorQuadModuleMap
```

Return whether the torsion quadratic modules `T` and `U` are isometric. If yes, it also returns an isometry $T \to U$.

If `T` and `U` are not semi-regular it requires that they both split into a direct sum of their respective quadratic radical (see [`radical_quadratic`](@ref)).

It requires that both `T` and `U` have modulus 1: in case one of them do not, they should be rescaled (see [`rescale`](@ref)).

# Examples

```jldoctest
julia> T = torsion_quadratic_module(QQ[2//3 2//3    0    0    0;
                                       2//3 2//3 2//3    0 2//3;
                                          0 2//3 2//3 2//3    0;
                                          0    0 2//3 2//3    0;
                                          0 2//3    0    0 2//3])
Finite quadratic module
  over integer ring
Abelian group: (Z/3)^5
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[2//3   2//3      0      0      0]
[2//3   2//3   2//3      0   2//3]
[   0   2//3   2//3   2//3      0]
[   0      0   2//3   2//3      0]
[   0   2//3      0      0   2//3]

julia> U = torsion_quadratic_module(QQ[4//3    0    0    0    0;
                                          0 4//3    0    0    0;
                                          0    0 4//3    0    0;
                                          0    0    0 4//3    0;
                                          0    0    0    0 4//3])
Finite quadratic module
  over integer ring
Abelian group: (Z/3)^5
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[4//3      0      0      0      0]
[   0   4//3      0      0      0]
[   0      0   4//3      0      0]
[   0      0      0   4//3      0]
[   0      0      0      0   4//3]

julia> bool, phi = is_isometric_with_isometry(T,U)
(true, Map: finite quadratic module -> finite quadratic module)

julia> is_bijective(phi)
true

julia> T2, _ = sub(T, [-T[4], T[2]+T[3]+T[5]])
(Finite quadratic module: (Z/3)^2 -> Q/2Z, Map: finite quadratic module -> finite quadratic module)

julia> U2, _ = sub(T, [T[4], T[2]+T[3]+T[5]])
(Finite quadratic module: (Z/3)^2 -> Q/2Z, Map: finite quadratic module -> finite quadratic module)

julia> bool, phi = is_isometric_with_isometry(U2, T2)
(true, Map: finite quadratic module -> finite quadratic module)

julia> is_bijective(phi)
true
```
