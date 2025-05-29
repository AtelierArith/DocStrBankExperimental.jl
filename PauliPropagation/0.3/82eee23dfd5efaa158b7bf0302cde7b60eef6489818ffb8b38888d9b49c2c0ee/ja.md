```
setpauli(
    pstr::PauliStringType, 
    target_paulis::Vector{Symbol}, 
    qinds::Vector{Integer}
)
```

整数パウリ文字列 `pstr` の `qinds` を `target_paulis` に設定します。`target_paulis` はシンボルのベクトルです。パフォーマンスが重要な関数では、タプルを使用してください。タプルは不変です。
