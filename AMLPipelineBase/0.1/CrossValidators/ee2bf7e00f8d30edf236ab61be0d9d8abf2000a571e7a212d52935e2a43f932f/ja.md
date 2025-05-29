```
crossvalidate(pl::Machine,X::DataFrame,Y::Vector,pfunc::Function,kfolds=10)
```

K-fold クロスバリデーションを実行します：

  * `pfunc` はパフォーマンスメトリックです
  * `X` と `Y` は入力とターゲットです
