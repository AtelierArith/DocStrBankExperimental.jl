```
ConvergenceCondition
```

非負スカラー値のシーケンス `val[0], val[1], val[2], ...` がある限界 `L` に収束したかどうかをチェックできるオブジェクトのための抽象型です。誤差 `err[iter] = |val[iter] - L|` が与えられます。

`ConvergenceCondition` のすべてのサブタイプは、`has_converged(::ConvergenceCondition, cache, val, err, iter)` を定義しなければなりません。デフォルトでは `nothing` に設定される `cache` は、収束を判断するために役立つ前の反復からの情報を保存するために使用される場合があります。特定の型の `cache` にアクセスするためには、`ConvergenceCondition` のサブタイプは `cache_type(::ConvergenceCondition, ::Type{FT})` を定義する必要があります。このキャッシュがどの反復で更新されるべきかを指定するためには、`needs_cache_update(::ConvergenceCondition, iter)` を定義する必要があります。これらの反復でキャッシュがどのように更新されるべきかを指定するためには、`updated_cache(::ConvergenceCondition, cache, val, err, iter)` を定義する必要があります。

`cache_type` は潜在的な型不安定エラーを防ぐために `promote_type` を呼び出すことができますが、ユーザーが型安定なコードを書くことを保証するために、これは避けるべきです。
