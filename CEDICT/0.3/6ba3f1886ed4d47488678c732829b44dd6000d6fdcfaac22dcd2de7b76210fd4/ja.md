```
search_senses(dict, keyword)
```

与えられた `keyword` を辞書の意味/感覚の中で検索します（`keyword` は定義の感覚の1つ以上に正確に現れなければなりません。この動作は将来のリリースで変更される可能性があります）。

## 例

```julia-repl
julia> search_senses(dict, "fishnet") .|> println;
漁網 (渔网): [yu2 wang3]
        fishing net
        fishnet
扳罾: [ban1 zeng1]
        to lift the fishnet
網襪 (网袜): [wang3 wa4]
        fishnet stockings
```
