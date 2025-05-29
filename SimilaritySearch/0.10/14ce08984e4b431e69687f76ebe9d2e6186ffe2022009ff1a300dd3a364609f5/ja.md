```
search(ex::ParallelExhaustiveSearch, q, res::KnnResult; minbatch=0, pools=nothing)
```

与えられたクエリ内のすべてのアイテムを評価してクエリを解決します。

# 引数

  * `ex`: 検索構造
  * `q`: 解決するクエリ
  * `res`: 結果セット

# キーワード引数

  * `minbatch`: 各スレッドごとに解決されるクエリの最小数、[`getminbatch`](@ref)を参照
  * `pools`: キャッシュのセット（このインデックスの場合は何もなし）
