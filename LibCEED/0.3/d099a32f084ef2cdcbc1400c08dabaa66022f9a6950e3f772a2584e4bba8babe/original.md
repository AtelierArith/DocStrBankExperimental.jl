```
takearray!(v::CeedVector, mtype::MemType)
```

Take ownership of the [`CeedVector`](@ref) array and remove the array from the [`CeedVector`](@ref). The caller is responsible for managing and freeing the array. The array is returns as a `Ptr{CeedScalar}`.
