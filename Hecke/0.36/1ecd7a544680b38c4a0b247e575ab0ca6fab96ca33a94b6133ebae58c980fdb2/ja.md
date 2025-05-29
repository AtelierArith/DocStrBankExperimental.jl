```
^(f::TorQuadModuleMap, n::Integer) -> TorQuadModuleMap
```

トーション二次モジュール `T` のアーベル群自己準同型 `f` が与えられたとき、`f` の $n$ 重自己合成を返します。

`n` は非負でなければならず、$f^0$ はデフォルトで `f` の定義域の単位写像です（[`identity_map`](@ref) を参照）。
