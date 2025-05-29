```
addparg!(fi::FuncInfo, name::Symbol [, index::Integer])
```

指定された `name` を持つ新しい引数を `FuncInfo` に追加し、位置引数に挿入します。 `index` が提供されていない場合、最後の非可変引数の位置に挿入します。新しい `SlotNumber` を返します。 `addarg!` + `insertparg!` と同等です。
