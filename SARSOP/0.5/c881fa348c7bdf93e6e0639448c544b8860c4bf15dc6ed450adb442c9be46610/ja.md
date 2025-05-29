```
PolicyGraphGenerator
```

  * `fast = false` は、.pomdpファイル用の高速（しかし非常に厳密な）代替パーサーを使用します
  * `graph_max_depth` 生成されるポリシーグラフの最大ホライズン。デフォルトでは制限はありません。
  * `graph_max_branch` 生成されるポリシーグラフの最大分岐数。表示されるのは確率が最も高いものです。デフォルトでは制限はありません。
  * `graph_min_prob` ポリシーグラフに分岐を表示するための最小確率閾値はゼロにデフォルト設定されています
  * `graph_filename` 生成されるDOTファイルの出力名
  * `pomdp_filename` pomdpファイルの入力
  * `policy_filename` ポリシーファイルの入力
