```
cheapest_insertion(distmat; ...)
```

単一都市ループを初期パスとして使用して、最も安い挿入法でツアーを完成させます。タプル `(path, cost)` を返します。

### オプションのキーワード引数:

  * `firstcity::Union{Int, Nothing}`: パスを開始する都市を指定します。`nothing`を渡すか、値を指定しないことはランダム選択に対応します。
  * `do2opt::Bool = true`: 2-optスワップによって見つかったパスを改善するかどうか。
