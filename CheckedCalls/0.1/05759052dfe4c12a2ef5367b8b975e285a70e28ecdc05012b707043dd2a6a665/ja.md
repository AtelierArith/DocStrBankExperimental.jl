```
throw_if_containsnan(r, f, args)
```

値 `r` が `f(args...)` の結果であり、`NaN` 値を含むかどうかをチェックし、含む場合は `ReturnValueContainsNaN` 例外をスローするユーティリティ関数です。

`throw_if_containsnan` は、自動微分中の計算オーバーヘッドを回避するために、特化した `ChainRulesCore.rrule` を備えています。
