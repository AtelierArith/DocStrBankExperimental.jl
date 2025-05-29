```
is_isometric_with_isometry(T::TorQuadModule, U::TorQuadModule)
                                               -> Bool, TorQuadModuleMap
```

トーション二次モジュール `T` と `U` が同型であるかどうかを返します。もしそうであれば、同型 $T \to U$ も返します。

`T` と `U` が半正則でない場合、両方がそれぞれの二次根の直和に分解される必要があります（[`radical_quadratic`](@ref)を参照）。

`T` と `U` の両方がモジュラス1である必要があります：どちらか一方がそうでない場合は、再スケーリングする必要があります（[`rescale`](@ref)を参照）。

# 例

```jldoctest
julia> T = torsion_quadratic_module(QQ[2//3 2//3    0    0    0;
                                       2//3 2//3 2//3    0 2//3;
                                          0 2//3 2//3 2//3    0;
                                          0    0 2//3 2//3    0;
                                          0 2//3    0    0 2//3])
有限二次モジュール
  整数環上
アーベル群: (Z/3)^5
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
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
有限二次モジュール
  整数環上
アーベル群: (Z/3)^5
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
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
