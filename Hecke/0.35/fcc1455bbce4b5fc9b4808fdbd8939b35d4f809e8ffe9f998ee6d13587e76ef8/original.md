```
idempotents(x::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, y::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> AbsSimpleNumFieldOrderElem, AbsSimpleNumFieldOrderElem
```

Returns a tuple `(e, f)` consisting of elements `e in x`, `f in y` such that `1 = e + f`.

If the ideals are not coprime, an error is raised.
