```
is_anti_isometric_with_anti_isometry(T::TorQuadModule, U::TorQuadModule)
                                                 -> Bool, TorQuadModuleMap
```

トーション二次モジュール `T` と `U` の間に反同型が存在するかどうかを返します。存在する場合、反同型 $T \to U$ を返します。

`T` と `U` が半正則でない場合、それぞれの二次根に対する直和に分解される必要があります（[`radical_quadratic`](@ref) を参照）。

`T` と `U` の両方がモジュラス1である必要があります：どちらか一方がそうでない場合、再スケーリングする必要があります（[`rescale`](@ref) を参照）。

# 例

```jldoctest
julia> T = torsion_quadratic_module(QQ[4//5;])
有限二次モジュール
  整数環上
アーベル群: Z/5
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
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
有限二次モジュール
  整数環上
アーベル群: Z/15
双線形値モジュール: Q/Z
二次値モジュール: Q/Z
グラム行列二次形式:
[3//5]

julia> bool, phi = is_anti_isometric_with_anti_isometry(T,T)
(true, Map: finite quadratic module -> finite quadratic module)

julia> a = gens(T)[1];

julia> a*a == -phi(a)*phi(a)
true
```
