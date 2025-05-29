```
rational_canonical_form(M::MatElem{T}) where T <: FieldElem -> MatElem{T}, MatElem{T}
```

行列 $C$ と $S$ を返します。ここで、$C = SMS^{-1}$ であり、$C$ は有理標準形です。
