```
one(a::MatrixElem{T}) where T <: NCRingElement
```

Return the identity matrix in the same matrix space as $a$. If the space does not contain square matrices, an error is thrown.
