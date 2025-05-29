```
is_norm(K::AbsSimpleNumField, a) -> Bool, AbsSimpleNumFieldElem
```

For $a$ an integer or rational, try to find $T \in K$ s.th. $N(T) = a$ holds. If successful, return true and $T$, otherwise false and some element. The element will be returned in factored form.
