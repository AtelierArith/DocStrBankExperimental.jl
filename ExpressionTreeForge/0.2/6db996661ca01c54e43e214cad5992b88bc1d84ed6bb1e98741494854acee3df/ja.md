```
evaluator = non_linear_JuMP_model_evaluator(expr_tree; variables::Vector{Int})
```

任意のサポートされている `expr_tree` に対して、`MathOptInterface.Nonlinear.Model` とその初期化された評価器を返します。`variables` は `expr_tree` に現れる変数のインデックスを示します。`variables` が提供されていない場合、`sort!(get_elemental_variables(expr_tree))` を通じて自動的に決定されます。**警告**: `variables` はソートされている必要があります！例:

```julia
expr_tree = :(x[1]^2 + x[3]^3)
variables = [1,3]
evaluator = non_linear_JuMP_model_evaluator(expr_tree; variables)
```

その後、次のようにして `expr_tree` から関数と勾配を評価できます:

```julia
x = rand(2)
MOI.eval_objective(evaluator, x)
grad = similar(x)
MOI.eval_objective_gradient(evaluator, grad, x)
```

**警告**: `x` のサイズは `expr_tree` の変数の数に依存し、最高の変数のインデックスには依存しません。
