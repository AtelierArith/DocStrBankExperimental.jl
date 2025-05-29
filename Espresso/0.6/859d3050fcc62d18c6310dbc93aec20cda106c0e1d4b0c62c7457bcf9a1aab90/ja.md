```julia
rewrite_all(ex, pat, rpat)

式の中のパターンのすべての出現を再帰的に書き換えます。例:

```

ex = :(foo(bar(foo(A)))) pat = :(foo(x)) rpat = :(quux(x)) rewrite_all(ex, pat, rpat; phs=[:x])

# ==> :(quux(bar(quux(A))))

```
