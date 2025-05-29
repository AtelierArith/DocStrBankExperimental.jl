```
print_expression_tree(nlp::NLPExpr)
```

Print a tree representation of the nonlinear expression `nlp`.

**Example**

```julia-repl
julia> expr = (x * sin(x)^3) / 2
(x * sin(x)^3) / 2

julia> print_expression_tree(expr)
/
├─ *
│  ├─ x
│  └─ ^
│     ├─ sin
│     │  └─ x
│     └─ 3
└─ 2
```
