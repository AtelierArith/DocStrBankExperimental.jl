```
DropNaN()
DropNaN(:)
```

テーブル内のNaN値を持つすべての行を削除します。

```
DropNaN(col₁, col₂, ..., colₙ)
DropNaN([col₁, col₂, ..., colₙ])
DropNaN((col₁, col₂, ..., colₙ))
```

選択した列 `col₁`, `col₂`, ..., `colₙ` にNaN値を持つすべての行を削除します。

```
DropNaN(regex)
```

`regex` に一致する列のNaN値を持つすべての行を削除します。

# 例

```julia
DropNaN(2, 3, 4)
DropNaN([:b, :c, :d])
DropNaN(("b", "c", "d"))
DropNaN(r"[bcd]")
```
