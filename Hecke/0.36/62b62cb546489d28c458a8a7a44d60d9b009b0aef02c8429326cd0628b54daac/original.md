```
is_norm(K::AbsSimpleNumField, a::ZZRingElem; extra::Vector{ZZRingElem}) -> Bool, AbsSimpleNumFieldElem
```

For a ZZRingElem $a$, try to find $T \in K$ s.th. $N(T) = a$ holds. If successful, return true and $T$, otherwise false and some element. In \testtt{extra} one can pass in additional prime numbers that are allowed to occur in the solution. This will then be supplemented. The element will be returned in factored form.
