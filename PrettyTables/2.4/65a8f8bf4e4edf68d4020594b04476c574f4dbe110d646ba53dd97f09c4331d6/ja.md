```
hl_row(i::Number, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

行 `i` 全体を `decoration` でハイライトします。

```
hl_row(rows::AbstractVector{Int}, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

`rows` のすべての行を `decoration` でハイライトします。

!!! info
    これらの関数は、HTML バックエンドで使用するための `MarkdownHighlighter` を返します。

