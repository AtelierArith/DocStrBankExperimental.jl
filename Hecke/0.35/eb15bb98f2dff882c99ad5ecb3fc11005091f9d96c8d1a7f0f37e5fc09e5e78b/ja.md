```
*(a::IntegerUnion, f::TorQuadModuleMap) -> TorQuadModuleMap
*(f::TorQuadModuleMap, a::IntegerUnion) -> TorQuadModuleMap
```

与えられた2つのトーション二次モジュール `T` と `U` の間のアーベル群準同型 `f` に対して、すべての要素 `b` を $h(b) := a*f(b)$ に送る点ごとの $a$-ツイスト準同型 `h` を返します。
