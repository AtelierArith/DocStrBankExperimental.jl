```
Multiline(args...)
```

各 `arg` を別々の行にレンダリングする `Multiline` オブジェクトを作成します。`Multiline` 値はセルの最上位の値としてのみ使用できるため、`Cell(Multiline(...))` は許可されますが、`Cell(Concat(Multiline(...), ...))` は許可されません。
