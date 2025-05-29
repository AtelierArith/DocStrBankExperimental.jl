rewrite_all(ex, rules)

Recursively rewrite an expression according to a list of rules like [pat => rpat] Example:

```
ex = :(foo(bar(foo(A))))
rules = [:(foo(x)) => :(quux(x)),
         :(bar(x)) => :(baz(x))]
rewrite_all(ex, rules; phs=[:x])
# ==> :(quux(baz(quux(A))))
```
