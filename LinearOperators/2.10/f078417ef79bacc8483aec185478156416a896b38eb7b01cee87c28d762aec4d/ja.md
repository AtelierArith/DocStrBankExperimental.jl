```
has_args5(op)
```

演算子が5引数の `mul!` で動作できるかどうかを判断します。`false` の場合、5引数の `mul!` の最初の呼び出し時にストレージベクトルが生成されます。3引数の `mul!` を使用する際には追加のベクトルは生成されません。
