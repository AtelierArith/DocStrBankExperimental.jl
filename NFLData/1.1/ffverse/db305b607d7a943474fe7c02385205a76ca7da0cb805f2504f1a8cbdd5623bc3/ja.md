```
load_ff_rankings(type::AbstractString = "draft")
```

現在のファンタジーフットボールランキングをFantasyPros.comからロードします。引数`type`には3つの有効なパラメータがあります：

  * `"draft"`：現在のファンタジーフットボールシーズンのドラフトリーグ用のFantasyProsランキング。デフォルトのパラメータです。
  * `"week"`：現在のファンタジーフットボールシーズンの週のプレイヤー用のFantasyProsランキング。
  * `"all"`：さまざまなフォーマットの歴史的なFantasyProsランキング。

このリソースに関する情報は、データ辞書を[こちら](https://nflreadr.nflverse.com/articles/dictionary_ff_rankings.html)でご覧ください。
