```
map_nlp_to_ast(map_func::Function, nlp::NLPExpr)::Expr
```

Map the nonlinear expression `nlp` to a Julia AST expression where each variable  is mapped via `map_func` and is directly interpolated into the AST expression.  This is intended as an internal method that can be helpful for developers that  wish to map a `NLPExpr` to a Julia AST expression that is compatible with  `JuMP.add_NL_expression`. 
