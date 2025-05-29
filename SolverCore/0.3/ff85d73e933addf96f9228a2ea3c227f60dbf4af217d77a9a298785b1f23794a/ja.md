```
reset!(solver::AbstractOptimizationSolver, model::AbstractNLPModel)
```

`solver` 構造体を再起動または再利用する文脈で使用します。`solve!` を同じ構造体で呼び出す前に、`model` に対して `solver` の内部フィールドをリセットします。`model` は、`solver` を初期化するために使用されたものと同じ数の変数、境界、および制約を持っている必要があります。
