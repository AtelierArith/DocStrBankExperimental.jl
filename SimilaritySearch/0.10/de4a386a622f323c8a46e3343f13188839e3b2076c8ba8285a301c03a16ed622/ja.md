```
index!(index::SearchGraph; parallel_block=get_parallel_block(), parallel_minimum_first_block=parallel_block, callbacks=SearchGraphCallbacks(verbose=index.verbose))
```

初期化されたデータベース（例えば、コンストラクタメソッドで与えられたもの）をインデックスします。これは並列または逐次的に行うことができます。引数は `append!` 関数と同じですが、内部の `index.db` を入力として使用します。
