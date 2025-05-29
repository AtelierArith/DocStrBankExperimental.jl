```
TorQuadModuleMap
```

トーション二次モジュール間のアーベル群準同型の型です。これは、`TorQuadModule`型の定義域と値域を追跡するヘッダーと、基礎となるアーベル群準同型を含みます。

# 例

```jldoctest
julia> L = rescale(root_lattice(:A,3), 3)
ランク3および次数3の整数格子
グラム行列
[ 6   -3    0]
[-3    6   -3]
[ 0   -3    6]

julia> T = discriminant_group(L)
有限二次モジュール
  整数環上
アーベル群: (Z/3)^2 x Z/12
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
[2//3      0   1//3]
[   0      0   2//3]
[1//3   2//3   1//4]

julia> N, f = normal_form(T)
(有限二次モジュール: (Z/3)^2 x Z/12 -> Q/2Z, マップ: 有限二次モジュール -> 有限二次モジュール)


julia> domain(f)
有限二次モジュール
  整数環上
アーベル群: (Z/3)^2 x Z/12
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
[2//3      0   1//3]
[   0      0   2//3]
[1//3   2//3   1//4]

julia> codomain(f)
有限二次モジュール
  整数環上
アーベル群: (Z/3)^2 x Z/12
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
[1//4      0      0      0]
[   0   4//3      0      0]
[   0      0   4//3      0]
[   0      0      0   4//3]

julia> abelian_group_homomorphism(f)
マップ
  (Z/3)^2 x Z/12 から
  4つの生成元と4つの関係を持つ有限生成アーベル群へ
```

`TorQuadModuleMap`型のオブジェクトは、トーション二次モジュールの準同型である必要はなく、すなわち、その定義域と値域のそれぞれの双線形または二次形式を保持する必要はありません。ただし、基礎となる有限アーベル群間の準同型である必要があります。

# 例

```jldoctest
julia> L = rescale(root_lattice(:A,3), 3);

julia> T = discriminant_group(L)
有限二次モジュール
  整数環上
アーベル群: (Z/3)^2 x Z/12
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
[2//3      0   1//3]
[   0      0   2//3]
[1//3   2//3   1//4]

julia> T6 = rescale(T, 6)
有限二次モジュール
  整数環上
アーベル群: (Z/3)^2 x Z/12
双線形値モジュール: Q/6Z
二次値モジュール: Q/12Z
グラム行列二次形式:
[4   0      2]
[0   0      4]
[2   4   3//2]

julia> f = hom(T, T6, gens(T6))
マップ
  有限二次モジュール: (Z/3)^2 x Z/12 -> Q/2Z から
  有限二次モジュール: (Z/3)^2 x Z/12 -> Q/12Z へ

julia> T[1]*T[1] == f(T[1])*f(T[1])
false

julia> is_bijective(f)
true
```

Heckeは、`TorQuadModuleMap`型のオブジェクトのためのいくつかのコンストラクタを提供しています。たとえば、[`hom(::TorQuadModule, ::TorQuadModule, ::ZZMatrix)`](@ref)、[`hom(::TorQuadModule, ::TorQuadModule, ::Vector{TorQuadModuleElem})`](@ref)、[`identity_map(::TorQuadModule)`](@ref)または[`trivial_morphism(::TorQuadModule)`](@ref)などです。
