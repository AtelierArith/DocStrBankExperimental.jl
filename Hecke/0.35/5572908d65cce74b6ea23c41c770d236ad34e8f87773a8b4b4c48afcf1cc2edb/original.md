```
is_principal_fac_elem(A::AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}) -> Bool, FacElem{AbsSimpleNumFieldElem, number_field}
```

Tests if $A$ is principal and returns $(\mathtt{true}, \alpha)$ if $A = \langle \alpha\rangle$ or $(\mathtt{false}, 1)$ otherwise. The generator will be in factored form.
