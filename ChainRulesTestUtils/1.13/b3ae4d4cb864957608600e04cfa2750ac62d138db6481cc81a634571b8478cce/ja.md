```
test_scalar(f, z; rtol=1e-9, atol=1e-9, fdm=central_fdm(5, 1), fkwargs=NamedTuple(), check_inferred=true, kwargs...)
```

スカラー入力とスカラー出力を持つ関数 `f` に対して、入力点 `z` で有限差分チェックを実行し、正しい `frule` と `rrule` が提供されていることを確認します。

# 引数

  * `f`: `frule` と `rrule` をテストする関数。
  * `z`: `f` を評価するための入力（一般的にはドメイン内の任意の点に設定されるべきです）。

# キーワード引数

  * `fdm`: 使用する有限差分法。
  * `fkwargs` は `f` にキーワード引数として渡されます。
  * `check_inferred=true` の場合、`frule` と `rrule` の推論可能性（型安定性）がチェックされます。
  * `testset_name`: 提供されている場合、テストをラップするために使用されるテストセットの名前。そうでない場合は、関数と引数の型から決定されます。
  * 残りのすべてのキーワード引数は `isapprox` に渡されます。
