```
is_invertible(A::AbsNumFieldOrderIdeal) -> Bool, AbsSimpleNumFieldOrderFractionalIdeal
```

Returns `true` and an inverse of $A$ or `false` and an ideal $B$ such that $A*B \subsetneq order(A)$, if $A$ is not invertible.
