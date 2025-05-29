```
apply_forest(forest::Ensemble, features::AbstractMatrix; use_multithreading=false)
```

学習したモデル `forest` を `features` に適用します。ここで `forest` は、例えば [`build_forest`](@ref) によって返される任意の `DecisionTree.Ensemble` インスタンスです。

# キーワード

  * `use_multithreading::Bool`: 利用可能な場合は複数のコアを使用するために `true`。デフォルトは `false` です。
