```
pseudo_matrix(m::Generic.Mat{AbsSimpleNumFieldOrderElem}, c::Vector{AbsNumFieldOrderIdeal{AbsSimpleNumField, AbsSimpleNumFieldElem}}) -> PMat{AbsSimpleNumFieldElem, AbsSimpleNumFieldOrderFractionalIdeal}
```

Returns the (row) pseudo matrix representing the $Z_k$-module  $\sum c_i m_i$  where $c_i$ are the ideals in $c$ and $m_i$ the rows of $M$.
