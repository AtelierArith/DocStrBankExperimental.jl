```
backwardselection!(model, folds, pool; verbose::Bool = false, optimality=mcc, kwargs...)
```

変数を1つずつ削除し、`optimality` 測定が増加しなくなるまで続けます。`pool` に含まれる変数は削除されません。

すべてのキーワード引数は `crossvalidate` と `train!` に渡されます。
