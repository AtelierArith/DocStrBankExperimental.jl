```
ordinalrank(x; lt=isless, by=identity, rev::Bool=false, ...)
```

配列の[順序付け](https://en.wikipedia.org/wiki/Ranking#Ordinal_ranking_.28.221234.22_ranking.29)（"1234" ランキング）を返します。`sort` 関数と同じキーワード引数をサポートしています。`x` のすべてのアイテムは、ソートされたベクトル内の位置に基づいて異なる連続したランクが与えられます。欠損値にはランク `missing` が割り当てられます。
