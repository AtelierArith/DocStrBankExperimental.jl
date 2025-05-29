```
parse_ternary_variable(error_fn, info_expr, lhs_sense, lhs, rhs_sense, rhs)
```

A hook for JuMP extensions to intercept the parsing of a `:comparison` expression, which has the form `lhs lhs_sense variable rhs_sense rhs`.
