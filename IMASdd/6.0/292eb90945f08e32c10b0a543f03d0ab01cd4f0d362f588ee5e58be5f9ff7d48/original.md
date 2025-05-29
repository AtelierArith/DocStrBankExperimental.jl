```
hasexpr(@nospecialize(ids::IDS), field::Symbol)
```

Returns true if the ids field has an expression.

Having an expression does not mean it –is– an expression. For that, use `isexpr(ids, field)`

NOTE: Does not evaluate expressions
