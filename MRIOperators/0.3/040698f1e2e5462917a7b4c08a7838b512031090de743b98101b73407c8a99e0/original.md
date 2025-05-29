```
SparseOp(type::T,name::AbstractString, shape::NTuple{N,Int64}; kargs...) where{N,T}
```

generates the sparsifying transform (`<: AbstractLinearOperator`) given its name.

# Arguments

  * `name::AbstractString`    - name of the sparsifying transform
  * `shape::NTuple{D,Int64}`  - size of the Array to be transformed
  * (`kargs`)                 - additional keyword arguments
