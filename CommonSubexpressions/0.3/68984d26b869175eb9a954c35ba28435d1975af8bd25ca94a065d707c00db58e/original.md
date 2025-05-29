```
@binarize(expr::Expr)
```

Convery all n-ary function calls within the given expression to nested binary calls to the same function. That is, convert all calls of the form `f(a, b, c)` to `f(f(a, b), c)` with as many layers of nesting as necessary. Operators like `+` and `*` are handled just like any other function call, so

```
@binarize a + b + c + d
```

will produce:

```
((a + b) + c) + d
```

This is intended to make subexpression elimination easier for long chained function calls, such as https://github.com/rdeits/CommonSubexpressions.jl/issues/14
