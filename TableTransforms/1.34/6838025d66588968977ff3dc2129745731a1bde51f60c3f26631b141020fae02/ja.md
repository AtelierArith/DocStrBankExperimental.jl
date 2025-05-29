```
Compose(; as=:coda)
```

テーブルのすべての列を新しい列 `as` の合成の部分に変換します。これは `CoDa.compose` 関数を使用します。

```
Compose(col₁, col₂, ..., colₙ; as=:coda)
Compose([col₁, col₂, ..., colₙ]; as=:coda)
Compose((col₁, col₂, ..., colₙ); as=:coda)
```

選択した列 `col₁`, `col₂`, ..., `colₙ` を合成の部分に変換します。

```
Compose(regex; as=:coda)
```

`regex` に一致する列を合成の部分に変換します。

# 例

```julia
Compose(as=:composition)
Compose([2, 3, 5])
Compose([:b, :c, :e])
Compose(("b", "c", "e"))
Compose(r"[bce]", as="composition")
```
