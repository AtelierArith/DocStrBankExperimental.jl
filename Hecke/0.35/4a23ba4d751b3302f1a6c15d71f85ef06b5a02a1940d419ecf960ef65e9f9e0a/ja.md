```
jordan_normal_form(M::MatElem{T}) where T <: FieldElem -> MatElem{T}, MatElem{T}
```

行列 $J$ と $S$ を返します。ここで $J = SMS^{-1}$ であり、$J$ はジョルダン標準形です。
