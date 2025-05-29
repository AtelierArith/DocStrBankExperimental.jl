```
is_anti_isometric_with_anti_isometry(T::TorQuadModule, U::TorQuadModule)
                                                 -> Bool, TorQuadModuleMap
```

Return whether there exists an anti-isometry between the torsion quadratic modules `T` and `U`. If yes, it returns such an anti-isometry $T \to U$.

If `T` and `U` are not semi-regular it requires that they both split into a direct sum of their respective quadratic radical (see [`radical_quadratic`](@ref)).

It requires that both `T` and `U` have modulus 1: in case one of them do not, they should be rescaled (see [`rescale`](@ref)).

# Examples

```jldoctest
julia> T = torsion_quadratic_module(QQ[4//5;])
Finite quadratic module
  over integer ring
Abelian group: Z/5
Bilinear value module: Q/Z
Quadratic value module: Q/2Z
Gram matrix quadratic form:
[4//5]

julia> bool, phi = is_anti_isometric_with_anti_isometry(T, T)
(true, Map: finite quadratic module -> finite quadratic module)

julia> a = gens(T)[1];

julia> a*a == -phi(a)*phi(a)
true

julia> G = matrix(QQ, 6, 6 , [3 3 0 0 0  0;
                                   3 3 3 0 3  0;
                                   0 3 3 3 0  0;
                                   0 0 3 3 0  0;
                                   0 3 0 0 3  0;
                                   0 0 0 0 0 10]);

julia> V = quadratic_space(QQ, G);

julia> B = matrix(QQ, 6, 6 , [1    0    0    0    0    0;
                              0 1//3 1//3 2//3 1//3    0;
                              0    0    1    0    0    0;
                              0    0    0    1    0    0;
                              0    0    0    0    1    0;
                              0    0    0    0    0 1//5]);


julia> M = lattice(V, B);

julia> B2 = matrix(QQ, 6, 6 , [ 1  0 -1  1  0 0;
                                     0  0  1 -1  0 0;
                                    -1  1  1 -1 -1 0;
                                     1 -1 -1  2  1 0;
                                     0  0 -1  1  1 0;
                                     0  0  0  0  0 1]);

julia> N = lattice(V, B2);

julia> T = torsion_quadratic_module(M, N)
Finite quadratic module
  over integer ring
Abelian group: Z/15
Bilinear value module: Q/Z
Quadratic value module: Q/Z
Gram matrix quadratic form:
[3//5]

julia> bool, phi = is_anti_isometric_with_anti_isometry(T,T)
(true, Map: finite quadratic module -> finite quadratic module)

julia> a = gens(T)[1];

julia> a*a == -phi(a)*phi(a)
true
```
