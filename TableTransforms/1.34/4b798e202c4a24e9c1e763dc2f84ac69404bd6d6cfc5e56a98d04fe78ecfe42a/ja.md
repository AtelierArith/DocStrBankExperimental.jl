```
DropMissing()
DropMissing(:)
```

テーブル内の欠損値を含むすべての行を削除します。

```
DropMissing(col₁, col₂, ..., colₙ)
DropMissing([col₁, col₂, ..., colₙ])
DropMissing((col₁, col₂, ..., colₙ))
```

選択した列 `col₁`, `col₂`, ..., `colₙ` に欠損値を含むすべての行を削除します。

```
DropMissing(regex)
```

`regex` に一致する列の欠損値を含むすべての行を削除します。

# 例

```julia
DropMissing()
DropMissing("b", "c", "e")
DropMissing([2, 3, 5])
DropMissing((:b, :c, :e))
DropMissing(r"[bce]")
```

## 注意事項

  * 変換により、列の要素型が `Union{Missing,T}` から `T` に変更されることがあります。
  * 変換された列が `missing` 値のみを含む場合、それは型 `Any` の空の列に変換されます。
