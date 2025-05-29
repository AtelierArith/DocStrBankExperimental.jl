```
列を選択する transform `col₁`, `col₂`, ..., `colₙ` を選択します。

```

Select(col₁ => newcol₁, col₂ => newcol₂, ..., colₙ => newcolₙ)

```

列 `col₁`, `col₂`, ..., `colₙ` を選択し、それらを `newcol₁`, `newcol₂`, ..., `newcolₙ` に名前変更します。

```

Select(regex)

```

`regex` に一致する列を選択します。

# 例

```

julia Select(1, 3, 5) Select([:a, :c, :e]) Select(("a", "c", "e")) Select(1 => :x, 3 => :y) Select(:a => :x, :b => :y) Select("a" => "x", "b" => "y") Select(r"[ace]") ```
