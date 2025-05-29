```
reduce_mod!(A::MatElem{T}, B::MatElem{T}) where T <: FieldElem
```

For a reduced row echelon matrix $B$, reduce the rows of $A$ modulo $B$, i.e. all the pivot columns will be zero afterwards.
