```
refarray(A::AbstractArray)
```

For a given array `A`, potentially return an optimized "ref array" representation of the original array, which can allow for faster comparison and sorting.

The default definition just returns the input array. This function is useful for custom array types which already store a "hashed"-like representation of elements where testing equality or permuting elements in place can be much faster than the original scalar value, like pooled arrays.

This generic function is owned by DataAPI.jl itself, which is the sole provider of the default definition.
