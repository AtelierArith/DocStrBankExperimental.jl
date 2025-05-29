```
evaluator = sparse_jacobian_JuMP_model(expr_trees)
```

Return the evaluator of a `MathOptInterface.Nonlinear.Model` defined by `expr_tree`, as long as it is supported. The `evaluator` considers the objective function as the sum of `expr_trees` and a constraint for each `expr_tree` contained in `expr_trees`. If the expression trees in `expr_trees` depend on a subset of variables, the Jacobian of the constraints will be sparse.
