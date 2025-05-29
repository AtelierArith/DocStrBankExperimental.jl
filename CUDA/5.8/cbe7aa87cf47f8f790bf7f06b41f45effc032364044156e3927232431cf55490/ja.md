```
name(err::CuError)
```

エラーコードの文字列表現を取得します。

```jldoctest
julia> err = CuError(CUDA.cudaError_enum(1))
CuError(CUDA_ERROR_INVALID_VALUE)

julia> name(err)
"ERROR_INVALID_VALUE"
```
