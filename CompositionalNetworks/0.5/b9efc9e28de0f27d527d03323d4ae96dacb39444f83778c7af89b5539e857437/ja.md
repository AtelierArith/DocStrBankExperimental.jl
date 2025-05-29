```
compose_to_file!(concept, name, path; domains, param = nothing, language = :Julia, search = :complete, global_iter = 10, local_iter = 100, metric = hamming, popSize = 200)
```

関数を探索し、学習し、ファイルに書き込みます。

# 引数:

  * `concept`: 学習する概念
  * `name`: 制約に付ける名前
  * `path`: 出力ファイルのパス

# キーワード引数:

  * `domains`: 探索空間を定義するドメイン
  * `param`: 制約のオプションのパラメータ
  * `language`: エクスポートする言語、デフォルトは `:julia`
  * `search`: `:partial` または `:complete` のいずれかの検索
  * `global_iter`: 学習の反復回数
  * `local_iter`: 遺伝的アルゴリズムにおける世代数
  * `metric`: 構成と既知の解との距離を測定するためのメトリック
  * `popSize`: 遺伝的アルゴリズムにおける集団のサイズ
