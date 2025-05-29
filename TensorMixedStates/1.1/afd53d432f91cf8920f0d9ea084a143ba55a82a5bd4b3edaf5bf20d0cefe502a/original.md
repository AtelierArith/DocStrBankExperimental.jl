```
matrix(a::ExprOp, site::AbstractSite...)
```

return the matrix of a generic operator for the given sites. If sites are all identical, you may give only one

# Examples

```
matrix(X, Qubit())
matrix(Swap, Qubit())
matrix(X⊗A, Qubit(), Boson(2))
```
