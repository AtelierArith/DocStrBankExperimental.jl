```
compare_expr([m=Main], lhs, rhs)
```

Compare two expression of type `Expr` or `Symbol` semantically, which:

1. ignore the detail value `LineNumberNode` in comparision;
2. ignore the detailed name of typevars declared by `where`;
3. recognize inserted objects and `Symbol`, e.g `:($Int)` is equal to `:(Int)`;
4. recognize `QuoteNode(:x)` and `Symbol("x")` as equal;
5. will guess module and type objects and compare their value directly  instead of their expression;

!!! tips
    This function is usually combined with [`prettify`](@ref) with `preserve_last_nothing=true` and `alias_gensym=false`.


This gives a way to compare two Julia expression semantically which means although some details of the expression is different but they should produce the same lowered code.
