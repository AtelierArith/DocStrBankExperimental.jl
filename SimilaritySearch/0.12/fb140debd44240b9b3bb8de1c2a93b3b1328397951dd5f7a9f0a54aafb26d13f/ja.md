```
find_neighborhood(copy_, index::SearchGraph{T}, context, item; hints=index.hints)
```

インデックス内の `item` の近傍を検索します。つまり、`item` がインデックスに存在する場合、そのアイテムが隣接すべきアイテムを検索します（内部関数）。`copy_` 関数は、返される KnnResult オブジェクトの扱いを制御するために強制されます。これは、指定されたコンテキストからのキャッシュ結果セットを使用します。

# 引数

  * `copy_`: コピー関数で、関数によって取得されるものを制御します。
  * `index`: 検索インデックス。
  * `item`: 挿入されるアイテム。
  * `context`: 使用されるコンテキスト、近傍、およびキャッシュオブジェクト
  * `hints`: 検索ヒント
