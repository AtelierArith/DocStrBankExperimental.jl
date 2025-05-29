rewrite_all(ex, pat, rpat)

Recursively rewrite all occurrences of a pattern in an expression. Example:

```
ex = :(foo(bar(foo(A))))
pat = :(foo(x))
rpat = :(quux(x))
rewrite_all(ex, pat, rpat; phs=[:x])
# ==> :(quux(bar(quux(A))))
```
