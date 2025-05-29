```
reduce_mod(A::MatElem{T}, B::MatElem{T}) where T <: FieldElem -> MatElem
```

For a reduced row echelon matrix $B$, reduce $A$ modulo $B$, i.e. all the pivot columns will be zero afterwards.
