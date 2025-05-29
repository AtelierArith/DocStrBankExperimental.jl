```
is_power(a::AbsSimpleNumFieldElem, n::Int; with_roots_unity::Bool = false) -> Bool, AbsSimpleNumFieldElem
```

Determines whether $a$ has an $n$-th root. If this is the case, the root is returned.

If the field $K$ is known to contain the $n$-th roots of unity, one can set `with_roots_unity` to `true`.
