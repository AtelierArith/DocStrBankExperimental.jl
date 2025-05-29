```
matrix(T::ITensor)
```

Given an ITensor `T` with two indices, returns a Matrix with a copy of the ITensor's elements, or a view in the case the ITensor's storage is Dense.

The ordering of the elements in the Matrix, in terms of which Index is treated as the row versus column, depends on the internal layout of the ITensor.

!!! warning
    This method is intended for developer use only and not recommended for use in ITensor applications unless you know what you are doing (for example you are certain of the memory ordering of the ITensor because you permuted the indices into a certain order).


See also [`array`](@ref), [`vector`](@ref).
