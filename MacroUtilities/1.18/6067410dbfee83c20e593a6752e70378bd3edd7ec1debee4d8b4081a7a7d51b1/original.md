```
FuncDef(; header, head, whereparams, return_type, body, line, doc)
```

Matches a function definition expression

# Fields

  * `header::FuncCall`
  * `head::Symbol`
  * `whereparams::Any = not_provided`
  * `return_type::Any = not_provided`
  * `body::Any`
  * `line::Union{LineNumberNode, NotProvided} = not_provided`
  * `doc::Union{Expr, String, NotProvided} = not_provided`
