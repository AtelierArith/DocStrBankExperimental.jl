```
slot!(b::Builder, name::Symbol; arg = false)::Core.SlotNumber
```

進行中の `Core.CodeInfo` に関連付けられた `name::Symbol` を持つ新しい `Core.SlotNumber` を `b::Builder` 内の `c::Canvas` に追加します。`arg == false` の場合、進行中の `Core.CodeInfo` の一貫性のために `Core.NewvarNode` で `pushfirst!` も実行します。（`arg` は新しいスロットを引数として解釈するかどうかを制御します）

`name::Symbol` はすでに `Core.SlotNumber` に関連付けられていてはいけません。
