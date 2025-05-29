```
append_items!(
    index::SearchGraph,
    context::SearchGraphContext,
    db
)
```

db内のすべてのアイテムをインデックスに追加します。これは並列または逐次的に行うことができます。

# 引数:

  * `index`: 検索グラフインデックス
  * `db`: 挿入するオブジェクトのコレクションで、`AbstractDatabase`が標準の入力ですが、任意の反復可能なオブジェクトをサポートします
  * `context`: グラフのコンテキスト環境、[`SearchGraphContext`](@ref)を参照してください。
