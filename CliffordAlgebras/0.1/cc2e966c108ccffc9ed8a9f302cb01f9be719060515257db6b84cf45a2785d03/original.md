```
Λᵏ(::MultiVector, ::Val{k}) where k
Λᵏ(::MultiVector, k::Integer)
```

Projects the MultiVector onto k-vectors. Similar to grade(mv,k), but uses @generated code and compile time optimizations.
