```
hl_row(i::Number, decoration::HtmlDecoration) -> HtmlHighlighter
```

行 `i` 全体を `decoration` でハイライトします。

```
hl_row(rows::AbstractVector{Int}, decoration::HtmlDecoration) -> HtmlHighlighter
```

`rows` 内のすべての行を `decoration` でハイライトします。

!!! info
    これらの関数は、HTML バックエンドで使用するための `HtmlHighlighter` を返します。

