```
load_player_stats(stat_type::AbstractString = "offense")
```

NFLFastR PBPデータから計算された個々の選手の統計をロードします。`stat_type`に`"offense"`、`"defense"`、または`"kicking"`のいずれかを渡すことで、返される統計のタイプを指定します。

このリソースに関する情報は、攻撃統計データ辞書を[こちら](https://nflreadr.nflverse.com/articles/dictionary_player_stats.html)で、守備統計データ辞書を[こちら](https://nflreadr.nflverse.com/articles/dictionary_player_stats_def.html)でご覧ください。
