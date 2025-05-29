```
@extomx(ex)
```

は、Julia式 `ex` をSymataに翻訳してコードに挿入します。これはSymataコードで使用されます。例えば、`algebra.jl`の`Collect`で使用されます。

`@extomx`は、結果のSymata式を評価しない点で`@sym`とは異なります。
