```
is_power(A::AbsNumFieldOrderIdeal, n::Int) -> Bool, AbsNumFieldOrderIdeal
is_power(A::AbsSimpleNumFieldOrderFractionalIdeal, n::Int) -> Bool, AbsSimpleNumFieldOrderFractionalIdeal
```

Computes, if possible, an ideal $B$ s.th. $B^n==A$ holds. In this case, `true` and $B$ are returned.
