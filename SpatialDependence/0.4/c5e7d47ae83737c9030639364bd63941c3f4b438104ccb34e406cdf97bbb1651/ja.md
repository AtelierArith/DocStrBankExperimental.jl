```
getisord(x, W)
```

Getis-Ord統計量を計算します。

# オプション引数

  * `star=true`: Gi*統計量を計算するか、`false`に設定するとGiを計算します。
  * `permutations=9999`: ランダム化テストのための置換の数。
  * `rng=default_rng()`: ランダム化テストのための乱数生成器。
