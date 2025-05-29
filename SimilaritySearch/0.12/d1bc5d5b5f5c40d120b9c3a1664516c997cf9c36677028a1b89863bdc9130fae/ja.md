```
index!(index::SearchGraph, context::SearchGraphContext)
```

初期化されたデータベース（例えば、コンストラクタメソッドで与えられたもの）をインデックスします。これは並列または逐次的に行うことができます。引数は `append_items!` 関数と同じですが、内部の `index.db` を入力として使用します。

# 引数:

  * `index`: グラフインデックス
  * `context`: グラフのコンテキスト環境、[`SearchGraphContext`](@ref)を参照してください。
