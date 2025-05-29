```
DropUnits()
DropUnits(:)
```

テーブル内のすべての列から単位を削除します。

```
DropUnits(col₁, col₂, ..., colₙ)
DropUnits([col₁, col₂, ..., colₙ])
DropUnits((col₁, col₂, ..., colₙ))
```

選択した列 `col₁`, `col₂`, ..., `colₙ` から単位を削除します。

```
DropUnits(regex)
```

`regex` に一致する列から単位を削除します。

# 例

```julia
DropUnits()
DropUnits([2, 3, 5])
DropUnits([:b, :c, :e])
DropUnits(("b", "c", "e"))
DropUnits(r"[bce]")
```
