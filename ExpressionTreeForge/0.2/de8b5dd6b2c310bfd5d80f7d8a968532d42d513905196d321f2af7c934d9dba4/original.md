```
expr = get_expression_tree(monlp::MathOptNLPModel)
expr = get_expression_tree(adnlp::ADNLPModel)
expr = get_expression_tree(model::JuMP.Model)
expr = get_expression_tree(evaluator::MOI.Nonlinear.Evaluator)
```

Return the objective function as a `Type_expr_tree` for: a `MathOptNLPModel`, a `ADNLPModel`, a `JuMP.Model` or a `MOI.Nonlinear.Evaluator`.
