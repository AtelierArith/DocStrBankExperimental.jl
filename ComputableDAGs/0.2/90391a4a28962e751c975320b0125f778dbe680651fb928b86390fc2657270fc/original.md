```
input_expr(problem_instance, name::String, input_symbol::Symbol)
```

For the given `problem_instance`, the entry node name, and the symbol of the problem input (where a variable of type `input_type(...)` will exist), return an `Expr` that gets that specific input value from the input symbol.

For more details on the `problem_instance`, please refer to the documentation.
