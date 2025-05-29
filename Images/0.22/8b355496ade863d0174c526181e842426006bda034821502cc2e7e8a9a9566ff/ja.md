```
entropy(logᵦ, img)
entropy(img; [kind=:shannon])
```

グレースケール画像のエントロピーを `-sum(p.*logᵦ(p))` として計算します。対数の底 β（すなわちエントロピー単位）は次のいずれかです：

  * `:shannon`（底 2 の対数、デフォルト）、または logᵦ = log2 を使用
  * `:nat`（底 e の対数）、または logᵦ = log を使用
  * `:hartley`（底 10 の対数）、または logᵦ = log10 を使用
