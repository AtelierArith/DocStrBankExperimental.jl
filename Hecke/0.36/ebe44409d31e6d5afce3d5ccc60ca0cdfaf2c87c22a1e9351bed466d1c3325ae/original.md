```
is_principal_with_data(A::AbsSimpleNumFieldOrderIdeal) -> Bool, AbsSimpleNumFieldOrderElem
is_principal_with_data(A::AbsSimpleNumFieldOrderFractionalIdeal) -> Bool, AbsSimpleNumFieldElem
```

Tests if $A$ is principal and returns $(\mathtt{true}, \alpha)$ if $A = \langle \alpha\rangle$ or $(\mathtt{false}, 1)$ otherwise.
