```
vector(T::ITensor)
```

Given an ITensor `T` with one index, returns a Vector with a copy of the ITensor's elements, or a view in the case the ITensor's storage is Dense.

See also [`array`](@ref), [`matrix`](@ref).
