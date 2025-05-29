```
jordan_normal_form(M::MatElem{T}) where T <: FieldElem -> MatElem{T}, MatElem{T}
```

Returns matrices $J$ and $S$ such that $J = SMS^{-1}$ and $J$ is in Jordan normal form.
