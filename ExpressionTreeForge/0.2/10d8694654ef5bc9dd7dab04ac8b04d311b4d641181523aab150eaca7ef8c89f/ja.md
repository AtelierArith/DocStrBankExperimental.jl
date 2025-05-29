```
evaluator = sparse_jacobian_JuMP_model(expr_trees)
```

`expr_tree`によって定義された`MathOptInterface.Nonlinear.Model`の評価者を返します。これはサポートされている限りです。`evaluator`は、`expr_trees`の合計として目的関数を考慮し、`expr_trees`に含まれる各`expr_tree`に対して制約を考慮します。`expr_trees`内の式木が変数のサブセットに依存している場合、制約のヤコビアンはスパースになります。
