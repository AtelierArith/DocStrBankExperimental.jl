```
is_principal_fac_elem(I::FacElem{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}, AbsNumFieldOrderIdealSet{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> Bool, FacElem{AbsSimpleNumFieldElem, number_field}
```

Tests if $I$ is principal and returns $(\mathtt{true}, \alpha)$ if $A = \langle \alpha\rangle$ or $(\mathtt{false}, 1)$ otherwise. The generator will be in factored form.
