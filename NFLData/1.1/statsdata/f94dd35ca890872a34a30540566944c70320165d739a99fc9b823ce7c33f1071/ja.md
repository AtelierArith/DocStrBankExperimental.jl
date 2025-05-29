```
load_nextgen_stats(stat_type::AbstractString = "passing")
```

週ごとにNGSデータをロードします。`stat_type`に次のいずれかを渡すことで返される統計の種類を指定します: `"passing"`、`"receiving"`、`"rushing"`。このリソースに関する情報は、データ辞書を[こちら](https://nflreadr.nflverse.com/articles/dictionary_nextgen_stats.html)でご覧ください。
