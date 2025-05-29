```
Concat(args...)
```

複数の値の表現を単一のテーブルセルに連結するために使用できる `Concat` オブジェクトを作成しますが、`args` の各 `arg` の変換セマンティクスはそのまま保持されます。

## 例

```julia
Concat(
    "Some text and an ",
    Annotated("annotated", "Some annotation"),
    " value",
)
# は "Some text and an annotated¹ value" としてレンダリングされます
```
