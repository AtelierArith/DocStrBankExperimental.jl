```
cnd::InterConditional
```

`Conditional`に似ていますが、呼び出し引数に課せられた手続き間の制約を伝えます。これは、論理エラーをキャッチするために`Conditional`とは別にされています：呼び出しを処理しているときの格子要素名は`InterConditional`であり、それ以外の場所では`Conditional`です。したがって、`InterConditional`は`CompilerTypes`には現れません—これらの型の使用は互いに分離されています—ただし、`InterConditional`のための格子を定義します。
