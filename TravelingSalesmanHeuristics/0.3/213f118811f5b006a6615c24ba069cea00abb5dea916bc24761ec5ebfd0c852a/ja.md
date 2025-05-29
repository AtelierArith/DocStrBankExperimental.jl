```
farthest_insertion(distmat; ...)
```

最遠挿入戦略を使用してTSPパスを生成します。`distmat`は正方形の実行列でなければなりません。タプル`(path, cost)`を返します。

### オプション引数:

  * `firstCity::Int`: パスを開始する都市を指定します。値を指定しない場合はランダム選択に対応します。
  * `do2opt::Bool = true`: 2-optスワップによってパスを改善するかどうか。
