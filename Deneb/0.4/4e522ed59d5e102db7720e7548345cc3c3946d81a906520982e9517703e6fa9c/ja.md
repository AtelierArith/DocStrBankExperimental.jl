```
Facet(; [row], , [column], kw...)
Facet(field; columns::Int=nothing, kw...)
```

ファセット仕様のための `FacetSpec` を作成します。 [](https://vega.github.io/vega-lite/docs/facet.html)。`field` は位置引数として渡すことができるか、`row`/`column` キーワード引数で渡す必要があります。

# 例

```
Facet("site:O", columns=2, sort=(op=:median, field=:yield))
Facet(row="Origin:N)
```
