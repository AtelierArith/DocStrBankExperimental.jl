```
protocolize(tns, protos...)
```

Create a `ProtocolizedArray` that accesses dimension `n` with protocol `protos[n]`, if `protos[n]` is not nothing. See the documention for [Iteration Protocols](@ref) for more information. For example, to gallop along the inner dimension of a matrix `A`, we write `A[gallop(i), j]`, which becomes `protocolize(A, gallop, nothing)[i, j]`.
