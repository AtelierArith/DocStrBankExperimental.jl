```
evaluate(p::Union{ZZPolyRingElem, QQPolyRingElem}, f::TorQuadModuleMap)
                                                      -> TorQuadModuleMap
```

与えられたトーション二次モジュール `T` のアーベル群自己準同型 `f` と整数係数を持つ単変数多項式 `p` に対して、変数を `f` に置き換えることによって得られる `T` のアーベル群自己準同型 $h := p(f)$ を返します。

`evaluate(p, f)` と書く代わりに、単に `p(f)` と呼ぶこともできます。
