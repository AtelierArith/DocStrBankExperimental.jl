```
parse_ternary_variable(error_fn, info_expr, lhs_sense, lhs, rhs_sense, rhs)
```

`:comparison` 式の解析を中断するための JuMP 拡張用のフックであり、形式は `lhs lhs_sense variable rhs_sense rhs` です。
