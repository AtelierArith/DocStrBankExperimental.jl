```
competerank(x; lt=isless, by=identity, rev::Bool=false, ...)
```

配列の[標準競技ランキング](http://en.wikipedia.org/wiki/Ranking#Standard_competition_ranking_.28.221224.22_ranking.29)（"1224"ランキング）を返します。`sort`関数と同じキーワード引数をサポートしています。等しい（*「タイ」*）項目には同じランクが与えられ、次のランクはタイの項目の数 - 1に等しいギャップの後に来ます。欠損値にはランク`missing`が割り当てられます。
