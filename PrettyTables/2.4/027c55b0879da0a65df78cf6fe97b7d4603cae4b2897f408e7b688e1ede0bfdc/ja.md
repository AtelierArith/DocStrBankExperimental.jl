```
hl_col(i::Number, decoration::HtmlDecoration) -> HtmlHighlighter
```

列 `i` 全体を `decoration` でハイライトします。

```
hl_col(cols::AbstractVector{Int}, decoration::HtmlDecoration) -> HtmlHighlighter
```

`cols` のすべての列を `decoration` でハイライトします。

!!! info
    これらの関数は、HTML バックエンドで使用するための `HtmlHighlighter` を返します。

