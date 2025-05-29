```
identity_matrix(M::MatElem{T}) where T <: NCRingElement
```

Construct the identity matrix in the same matrix space as `M`, i.e. with ones down the diagonal and zeroes elsewhere. `M` must be square. This is an alias for `one(M)`.
