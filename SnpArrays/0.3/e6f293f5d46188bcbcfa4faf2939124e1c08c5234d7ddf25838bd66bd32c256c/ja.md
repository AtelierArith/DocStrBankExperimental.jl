```
kinship_pruning(grm::Matrix; method=:bottom_up, cutoff=0.125, min_samples=0)
```

親族プルーニング後に残るサンプルを示すBitVectorを返します。`method`の有効な値は`:bottom_up`、`:top_down`、`:gcta`、および`:plink`です。`min_samples`が定義されている場合、その数のサンプルが残るとプルーニングは停止します。

  * `:bottom_up`はボトムアップの貪欲法を実行し、最も低い次数のサンプルの隣接サンプルを反復的に排除します。
  * `:top_down`はトップダウンの貪欲法を実行し、最も高い次数のサンプルを反復的に排除します。
  * `:gcta`はGCTAで実装された方法を実行します。
  * `:plink`はPLINKで実装された方法を実行します。

一般的に、`:bottom_up`の貪欲法は最も良いパフォーマンスを発揮し（最も多くの被験者を保持）、保証された近似比を持っています。`min_samples`が定義されている場合、`:top_down`の貪欲法はオフダイアゴナル値の最も少ない数を保持します。
