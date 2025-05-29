```
array(T::ITensor, inds...)
```

Convert an ITensor `T` to an Array.

The ordering of the elements in the Array are specified by the input indices `inds`. This tries to avoid copying of possible (i.e. may return a view of the original data), for example if the ITensor's storage is Dense and the indices are already in the specified ordering so that no permutation is required.

!!! warning
    Note that in the future we may return specialized AbstractArray types for certain storage types, for example a `LinearAlgebra.Diagonal` type for an ITensor with `Diag` storage. The specific storage type shouldn't be relied upon.


See also [`matrix`](@ref), [`vector`](@ref).
