```
unname(A::NamedDimsArray) -> AbstractArray
unname(A) === A
```

Return the input array `A` without any dimension names.

For `NamedDimsArray`s this returns the parent array, equivalent to calling `parent`, but for anything else it simply returns the input.

Supports some LinearAlgebra wrappers LowerTriangular, UpperTriangular such that `unname(x::UpperTriangular{T, <:NamedDimsArray}) == unname(parent(x))
