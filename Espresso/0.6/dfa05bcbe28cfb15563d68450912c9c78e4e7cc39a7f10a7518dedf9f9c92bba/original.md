Substitute symbols in `ex` according to substitute table `st`. Example:

```
ex = :(x ^ n)
subs(ex, x=2)            # ==> :(2 ^ n)
```

alternatively:

```
subs(ex, Dict(:x => 2))  # ==> :(2 ^ n)
```

If `ex` contains a :(xs...) argument and `st` contains an array-valued sabstitute for it, the substitute will be flattened:

```
ex = :(foo(xs...))
subs(ex, Dict(:xs => [:a, :b, :c]))
# ==> :(foo(a, b, c))
```
