```
setpauli(
    pstr::PauliStringType, 
    target_paulis::PauliStringType, 
    qinds::Vector{Integer}
)
```

整数パウリ文字列 `pstr` の `qinds` を `target_paulis` に設定します。パフォーマンスが重要な関数では、`qinds` にタプルを使用してください。タプルは不変です。
