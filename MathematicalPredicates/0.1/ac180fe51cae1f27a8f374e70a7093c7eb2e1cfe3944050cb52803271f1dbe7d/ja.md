```
evaluate(p::Predicate, args...)
```

与えられた引数に対して述語を評価します。

### 入力

  * `p`    – 述語
  * `args` – 引数リスト

### 出力

`p(args)`の評価に対応する`Bool`。

### 注意事項

`evaluate(p, args)`の短縮版として`p(args)`を提供しています。
