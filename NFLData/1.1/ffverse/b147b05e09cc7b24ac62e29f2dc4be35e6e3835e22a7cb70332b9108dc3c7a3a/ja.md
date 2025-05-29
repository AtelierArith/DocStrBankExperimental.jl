```
function load_ff_opportunity(seasons::Number = most_recent_season(), stat_type::AbstractString = "weekly", model_version::AbstractString = "latest")
```

指定されたシーズンのFFOpportunityデータセットをロードします。`seasons`はデータを取得する年を示し、デフォルトでは最近プレイされたNFLシーズンになります。すべての利用可能なシーズンを取得するには、`seasons = true`を渡します。`stat_type`は3つの潜在的な引数を取ります：

  * `"weekly"`: FFOpportunityの完全なデータを週ごとに取得します。デフォルトのオプションです。
  * `"pbp_pass"`: FFOpportunityのパッシングデータを週ごとに取得します。
  * `"pbp_rush"`: FFOpportunityのラッシングデータを週ごとに取得します。

`model_version`は2つの潜在的な引数を取ります：

  * `"latest"`: 最新のFFOpportunityモデルによって生成されたデータを取得します。
  * `"v1.0.0"`: 元のFFOpportunityモデルによって生成されたデータを取得します。

このリソースに関する情報は、データ辞書を[こちら](https://nflreadr.nflverse.com/articles/dictionary_ff_opportunity.html)でご覧ください。
