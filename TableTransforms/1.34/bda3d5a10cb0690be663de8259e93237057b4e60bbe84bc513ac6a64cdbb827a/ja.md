```
Sort(col₁, col₂, ..., colₙ; kwargs...)
Sort([col₁, col₂, ..., colₙ]; kwargs...)
Sort((col₁, col₂, ..., colₙ); kwargs...)
```

選択した列 `col₁`, `col₂`, ..., `colₙ` の行を `kwargs` を `sortperm` 関数に渡してソートします。

```
Sort(regex; kwargs...)
```

`regex` に一致する列の行をソートします。

# 例

```julia
Sort(:a)
Sort(:a, :c, rev=true)
Sort([1, 3, 5], by=row -> abs.(row))
Sort(("a", "c", "e"))
Sort(r"[ace]")
```
