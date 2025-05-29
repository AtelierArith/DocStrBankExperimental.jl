```
load_pfr_advstats(seasons = most_recent_season(), stat_type::String = "pass", summary_level::String = "week")
```

指定されたシーズンの[Pro-Football-Reference.com](https://www.pro-football-reference.com/)から高度な統計をロードします。デフォルトでは、最も最近のシーズンが使用されます。すべての利用可能なシーズンを取得するには、`seasons = true`を渡してください。

`stat_type`に`"pass"`、`"rush"`、`"rec"`、または`"def"`のいずれかを渡すことで、返される統計のタイプを指定します。

`summary_level`に`"week"`または`"season"`のいずれかを渡すことで、返される統計の要約レベルを指定します。

このリソースに関する情報は、データ辞書[こちら](https://nflreadr.nflverse.com/articles/dictionary_pfr_passing.html)を参照してください。
