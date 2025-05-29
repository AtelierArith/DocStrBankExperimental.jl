```
tensor(a::ExprOp, site::AbstractSite...)
```

return the ITensor of a generic operator for the given sites. If sites are all identical, you may give only one

# Examples

```
tensor(X, Qubit())
tensor(Swap, Qubit())
tensor(X⊗A, Qubit(), Boson(2))
```
