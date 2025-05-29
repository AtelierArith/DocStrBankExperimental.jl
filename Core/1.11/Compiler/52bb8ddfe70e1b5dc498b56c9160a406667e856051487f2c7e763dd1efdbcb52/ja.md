```
stmts_awaiting_insertion(compact::IncrementalCompact, idx::Int)
```

`compact`の`1:idx`の範囲内の任意の命令に挿入のためにキューに入れられた新しい/保留中の命令がある場合はtrueを返します。それ以外の場合はfalseを返します。
