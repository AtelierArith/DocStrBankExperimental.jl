```
consgrouped_ptrs(A::AbstractVector)
```

Compute an element pointer vector, suitable for creation of a `VectorOfVectors` that implies grouping equal consecutive entries of `A`.

Example:

```julia
    A = [1, 1, 2, 3, 3, 2, 2, 2]
    elem_ptr = consgrouped_ptrs(A)
    first.(VectorOfVectors(A, elem_ptr)) == [1, 2, 3, 2]
```

consgrouped*ptrs Typically, `elem*ptr` will be used to apply the computed grouping to other data:

```julia
    B = [1, 2, 3, 4, 5, 6, 7, 8]
    VectorOfVectors(B, elem_ptr) == [[1, 2], [3], [4, 5], [6, 7, 8]]
```
