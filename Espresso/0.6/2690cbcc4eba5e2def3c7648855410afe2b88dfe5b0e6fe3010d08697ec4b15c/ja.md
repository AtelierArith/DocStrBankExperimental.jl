rewrite_all(ex, rules)

式をルールのリストに従って再帰的に書き換えます。例: [pat => rpat] 

```
ex = :(foo(bar(foo(A))))
rules = [:(foo(x)) => :(quux(x)),
         :(bar(x)) => :(baz(x))]
rewrite_all(ex, rules; phs=[:x])
# ==> :(quux(baz(quux(A))))
```
