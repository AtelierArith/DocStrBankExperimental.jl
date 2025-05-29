```
name(err::CuError)
```

Gets the string representation of an error code.

```jldoctest
julia> err = CuError(CUDA.cudaError_enum(1))
CuError(CUDA_ERROR_INVALID_VALUE)

julia> name(err)
"ERROR_INVALID_VALUE"
```
