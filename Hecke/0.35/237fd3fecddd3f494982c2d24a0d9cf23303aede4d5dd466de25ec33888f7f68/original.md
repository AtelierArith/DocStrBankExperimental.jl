```
is_index_divisor(O::AbsSimpleNumFieldOrder, d::ZZRingElem) -> Bool
is_index_divisor(O::AbsSimpleNumFieldOrder, d::Int) -> Bool
```

Returns whether $d$ is a divisor of the index of $\mathcal O$. It is assumed that $\mathcal O$ contains the equation order of the ambient number field.
