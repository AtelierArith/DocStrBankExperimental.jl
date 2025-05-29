```
array(T::ITensor)
```

Given an ITensor `T`, returns an Array with a copy of the ITensor's elements, or a view in the case the the ITensor's storage is Dense.

The ordering of the elements in the Array, in terms of which Index is treated as the row versus column, depends on the internal layout of the ITensor.

!!! warning
    This method is intended for developer use only and not recommended for use in ITensor applications unless you know what you are doing (for example you are certain of the memory ordering of the ITensor because you permuted the indices into a certain order).


See also [`matrix`](@ref), [`vector`](@ref).
