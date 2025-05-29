```
to_align(align[, error_prefix])
```

指定された align を `Vec2f` に変換します。`VecTypes{2}` と `Real` および `Symbol` 要素を持つ二成分の `Tuple` を変換できます。

カスタムエラーメッセージを指定するには、`error_prefix` を追加するか、それぞれ `halign2num(value, error_msg)` と `valign2num(value, error_msg)` を使用できます。
