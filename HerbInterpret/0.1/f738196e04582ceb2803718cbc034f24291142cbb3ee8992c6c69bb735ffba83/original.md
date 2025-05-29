```
interpret(tab::SymbolTable, ex::Expr)
```

Evaluates an expression without compiling it. Uses AST and symbol lookups. Only supports :call and :(=) expressions at the moment.

Example usage:

```
tab = SymbolTable(:f => f, :x => x)
ex = :(f(x))
interpret(tab, ex)
```

WARNING: This function throws exceptions that are caused in the given expression. These exceptions have to be handled by the caller of this function.
