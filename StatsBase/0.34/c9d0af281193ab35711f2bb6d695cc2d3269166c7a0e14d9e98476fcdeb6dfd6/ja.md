```
denserank(x; lt=isless, by=identity, rev::Bool=false, ...)
```

配列の[dense ranking](http://en.wikipedia.org/wiki/Ranking#Dense_ranking_.28.221223.22_ranking.29)（"1223" ランキング）を返します。`sort` 関数と同じキーワード引数をサポートしています。等しいアイテムには同じランクが与えられ、次のランクはギャップなしで割り当てられます。欠損値にはランク `missing` が割り当てられます。
