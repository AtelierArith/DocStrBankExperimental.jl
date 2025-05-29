```
jordan_decomposition(M::MatElem{T}) where T <:FieldElem -> MatElem{T}, MatElem{T}
```

行列 $S$ と $N$ を返します。ここで、$N$ は nilpotent であり、$S$ は semisimple であり、$M = S+N$ です。
