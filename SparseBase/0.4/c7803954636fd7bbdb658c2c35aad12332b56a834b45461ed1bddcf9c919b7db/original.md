```
hasfixedsparsity(::Type{A})::Bool
```

True if the sparsity pattern of the type `A` may be changed. A `Diagonal` type, for instance, may not have its sparsity pattern changed.
