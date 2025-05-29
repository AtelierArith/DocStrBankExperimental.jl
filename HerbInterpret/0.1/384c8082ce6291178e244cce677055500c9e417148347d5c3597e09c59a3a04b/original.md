```
execute_on_input(tab::SymbolTable, expr::Any, input::Dict{Symbol, T})::Any where T
```

Evaluates an expression `expr` within the context of a symbol table `tab` and a single input dictionary `input`.  The input dictionary keys should match the symbols used in the expression, and their values are used during the expression's evaluation.

# Arguments

  * `tab::SymbolTable`: A symbol table containing predefined symbols and their associated values or functions.
  * `expr::Any`: The expression to be evaluated. Can be any Julia expression that is valid within the context of the provided symbol table and input.
  * `input::Dict{Symbol, T}`: A dictionary where each key is a symbol used in the expression, and the value is the corresponding value to be used in the expression's evaluation. The type `T` can be any type.

# Returns

  * `Any`: The result of evaluating the expression with the given symbol table and input dictionary.

!!! warning
    This function throws exceptions that are caused in the given expression. These exceptions have to be handled by the caller of this function.

