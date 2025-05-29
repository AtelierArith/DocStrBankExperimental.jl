```
multiplicative_jordan_decomposition(M::MatElem{T}) where T <:FieldElem -> MatElem{T}, MatElem{T}
```

行列 $S$ と $U$ を返します。ここで、$U$ は単位的であり、$S$ は半単純であり、$M = SU$ です。
