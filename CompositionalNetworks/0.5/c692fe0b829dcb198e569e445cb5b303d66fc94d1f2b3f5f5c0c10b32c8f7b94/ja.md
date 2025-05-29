```
explore_learn_compose(concept; domains, param = nothing, search = :complete, global_iter = 10, local_iter = 100, metric = hamming, popSize = 200, action = :composition)
```

探索空間を調査し、ICNから構成を学び、エラーファンクションを構成します。

# 引数:

  * `concept`: 対象制約の概念
  * `domains`: トレーニング空間を定義する変数のドメイン
  * `param`: 制約のオプションパラメータ
  * `search`: `flexible`、`:partial`、または `:complete` 検索のいずれか。柔軟な検索は `search_limit` と `solutions_limit` を使用して、検索空間を部分的または完全に探索する必要があるかどうかを判断します
  * `global_iter`: 学習の反復回数
  * `local_iter`: 遺伝的アルゴリズムにおける世代数
  * `metric`: 構成と既知の解の間の距離を測定するためのメトリック
  * `popSize`: 遺伝的アルゴリズムにおける集団のサイズ
  * `action`: 構成の説明を得るための `:symbols` または 構成された関数自体を得るための `:composition` のいずれか
