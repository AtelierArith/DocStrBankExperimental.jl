```
evaluate!(cache,f,x...)
```

与えられた `cache` オブジェクトに提供されたスクラッチデータを使用して、引数 `x...` に対してマッピング `f` を適用します。`cache` オブジェクトは、`x` と同じ型の引数を使用して [`return_cache`](@ref) 関数で構築されます。一般に、返される値 `y` は `cache` オブジェクトの状態の一部を共有することがあります。この関数への2回以上の呼び出しの結果に同時にアクセスする必要がある場合（例えば、マルチスレッドで）、複数の `cache` オブジェクトを作成して使用します（例えば、スレッドごとに1つのキャッシュ）。
