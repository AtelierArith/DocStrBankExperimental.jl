```
expr = get_expression_tree(monlp::MathOptNLPModel)
expr = get_expression_tree(adnlp::ADNLPModel)
expr = get_expression_tree(model::JuMP.Model)
expr = get_expression_tree(evaluator::MOI.Nonlinear.Evaluator)
```

目的関数を `MathOptNLPModel`、`ADNLPModel`、`JuMP.Model` または `MOI.Nonlinear.Evaluator` のための `Type_expr_tree` として返します。
