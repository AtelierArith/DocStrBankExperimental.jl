```
code_expr(f, types)
```

Returns the expression for the method definition for `f` with the specified types.

May return `nothing` if Revise isn't loaded. In such cases, calling `Meta.parse(code_string(f, types))` can sometimes be an alternative.
