```
map_nlp_to_ast(map_func::Function, nlp::NLPExpr)::Expr
```

非線形式 `nlp` を Julia AST 式にマップします。ここで、各変数は `map_func` を介してマップされ、AST 式に直接補間されます。これは、`NLPExpr` を `JuMP.add_NL_expression` と互換性のある Julia AST 式にマップしたい開発者にとって役立つ内部メソッドとして意図されています。
