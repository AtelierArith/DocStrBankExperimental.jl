```
forwardselection!(model, folds; verbose::Bool = false, optimality=mcc, kwargs...)
```

変数を1つずつ追加し、`optimality` 測定が増加しなくなるまで続けます。

すべてのキーワード引数は `crossvalidate` と `train!` に渡されます。
