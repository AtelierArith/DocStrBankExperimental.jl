```
forwardselection!(model, folds, pool; verbose::Bool = false, optimality=mcc, kwargs...)
```

変数を1つずつ追加し、`optimality` 測定が増加しなくなるまで続けます。`pool` にある変数は最初に追加されます。

すべてのキーワード引数は `crossvalidate` と `train!` に渡されます。
