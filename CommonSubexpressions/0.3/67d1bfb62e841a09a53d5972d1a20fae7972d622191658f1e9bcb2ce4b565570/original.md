```
@cse(expr; warn=true)
```

Perform naive common subexpression elimination under the assumption that all functions called withing the body of the macro are pure, meaning that they have no side effects. See [Readme.md](https://github.com/rdeits/CommonSubexpressions.jl/blob/master/Readme.md) for more details.

This macro will recursively expand macro calls within the expression before performing subexpression elimination. A useful macro to combine with this is `@binarize`, which will turn n-ary function calls into nested binary calls and can therefore provide more opportunities for subexpression elimination. Usage:

```
@cse(@binarize(<your code here>))
```

If the macro encounters an expression which it does not know how to handle, it will return that expression unmodified. If `warn=true`, then it will also log a warning in that event.
