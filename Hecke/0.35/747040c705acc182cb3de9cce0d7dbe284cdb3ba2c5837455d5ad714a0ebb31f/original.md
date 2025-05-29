```
sunit_group_fac_elem(I::Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> GrpAb, Map
```

For an array $I$ of (coprime prime) ideals, find the $S$-unit group defined by $I$, ie. the group of non-zero field elements which are only divisible by ideals in $I$. The map will return elements in factored form.
