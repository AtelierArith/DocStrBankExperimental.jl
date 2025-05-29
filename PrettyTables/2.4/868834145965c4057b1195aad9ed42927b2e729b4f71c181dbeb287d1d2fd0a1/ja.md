```
hl_col(i::Number, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

列 `i` 全体を `decoration` でハイライトします。

```
hl_col(cols::AbstractVector{Int}, decoration::MarkdownDecoration) -> MarkdownHighlighter
```

`cols` のすべての列を `decoration` でハイライトします。

!!! info
    これらの関数は、HTML バックエンドで使用するための `MarkdownHighlighter` を返します。

