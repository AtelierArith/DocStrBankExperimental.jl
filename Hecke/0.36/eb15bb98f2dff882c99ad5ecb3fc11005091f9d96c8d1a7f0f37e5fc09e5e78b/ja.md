```
*(a::IntegerUnion, f::TorQuadModuleMap) -> TorQuadModuleMap
*(f::TorQuadModuleMap, a::IntegerUnion) -> TorQuadModuleMap
```

与えられたアーベル群準同型 `f` が2つのトーション二次モジュール `T` と `U` の間にあるとき、すべての要素 `b` を $h(b) := a*f(b)$ に送る `f` の点ごとの $a$-ツイスト準同型 `h` を返します。
