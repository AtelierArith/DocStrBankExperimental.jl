```
@symExpr(expr)
```

Symata-evaluates `expr`, translates the result to a Julia expression, and inserts it into the surrounding code. This works just like any Julia macro for inserting code, except that the code is generated by evaluating a Symata expression.

The following evaluates Symata code, translates the result to Julia and uses it as the body of a Julia function.

```
julia> f1(z) = @symExpr Together(PolyLog(-1,z) + (1-z))
```
