```
evaluator = non_linear_JuMP_model_evaluator(expr_tree; variables::Vector{Int})
```

Return a `MathOptInterface.Nonlinear.Model` and its initialized evaluator for any `expr_tree` supported. `variables` informs the indices of the variables appearing in `expr_tree`. If `variables` is not provided, it is determined automatically through `sort!(get_elemental_variables(expr_tree))`. **Warning**: `variables` must be sorted! Example:

```julia
expr_tree = :(x[1]^2 + x[3]^3)
variables = [1,3]
evaluator = non_linear_JuMP_model_evaluator(expr_tree; variables)
```

Afterward, you may evaluate the function and the gradient from `expr_tree` with:

```julia
x = rand(2)
MOI.eval_objective(evaluator, x)
grad = similar(x)
MOI.eval_objective_gradient(evaluator, grad, x)
```

**Warning**: The size of `x` depends on the number of variables of `expr_tree` and not from the highest variable's index.
