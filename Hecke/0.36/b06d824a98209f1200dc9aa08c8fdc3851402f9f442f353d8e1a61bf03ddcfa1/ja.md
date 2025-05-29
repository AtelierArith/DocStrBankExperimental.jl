```
torsion_quadratic_module(q::QQMatrix) -> TorQuadModule
```

与えられたグラム行列 `q` によるトーション二次モジュールを返します。もし `q` の対角成分がすべて、偶数の分子または偶数の分母を持つ場合、二次形式の値モジュールは `Q/2Z` になります。

# 例

```jldoctest
julia> torsion_quadratic_module(QQ[1//6;])
有限二次モジュール
  整数環上
アーベル群: Z/6
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
[1//6]

julia> torsion_quadratic_module(QQ[1//2;])
有限二次モジュール
  整数環上
アーベル群: Z/2
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
[1//2]

julia> torsion_quadratic_module(QQ[3//2;])
有限二次モジュール
  整数環上
アーベル群: Z/2
双線形値モジュール: Q/Z
二次値モジュール: Q/2Z
グラム行列二次形式:
[3//2]

julia> torsion_quadratic_module(QQ[1//3;])
有限二次モジュール
  整数環上
アーベル群: Z/3
双線形値モジュール: Q/Z
二次値モジュール: Q/Z
グラム行列二次形式:
[1//3]
```
