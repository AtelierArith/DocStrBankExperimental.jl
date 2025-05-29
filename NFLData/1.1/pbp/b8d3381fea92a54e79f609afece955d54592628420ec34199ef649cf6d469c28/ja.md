```
load_participation(seasons = 2023, include_pbp::Bool = false)
```

**通知:** NFLは2023シーズンの参加データの公開量を制限し、2024シーズンのデータ提供を停止しました。2023シーズンは完全なカバレッジが欠けており、2024シーズンおよび今後のシーズンはデータが更新される可能性は低いです。

特定のシーズンのNGS参加データをロードします。デフォルトは2023シーズンです。すべての利用可能なシーズンのためには`seasons = true`を渡してください。この参加データを`load_pbp()`によって提供されるPBPデータに結合するには、この関数に`include_pbp=true`を渡してください。

このリソースに関する情報は、データ辞書を[こちら](https://nflreadr.nflverse.com/articles/dictionary_participation.html)でご覧ください。
