```
hcat(A::MatrixElem{T}...) where T <: NCRingElement -> MatrixElem
```

Return the horizontal concatenating of the matrices $A$. All component matrices need to have the same base ring and number of rows.
