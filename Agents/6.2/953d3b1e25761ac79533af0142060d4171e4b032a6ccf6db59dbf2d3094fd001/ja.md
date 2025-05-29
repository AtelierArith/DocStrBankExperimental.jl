```
ensemblerun!(generator, n; kwargs...)
```

多くの `ABM` を生成し、提供された `generator` を使用して `ensemblerun!(models, ...)` に伝播させます。この `generator` は、入力がシードの一引数関数です。

このメソッドには追加のキーワード `ensemble = 5, seeds = rand(UInt32, ensemble)` があります。
