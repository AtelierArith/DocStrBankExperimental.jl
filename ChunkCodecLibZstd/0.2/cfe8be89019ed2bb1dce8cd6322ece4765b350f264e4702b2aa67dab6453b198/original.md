```
ZSTD_cParam_getBounds(cParam::Int32)::ZSTD_bounds
```

All parameters must belong to an interval with lower and upper bounds, otherwise they will either trigger an error or be automatically clamped. Return : a structure, [`ZSTD_bounds`](@ref), which contains

  * an error status field, which must be tested using [`ZSTD_isError`](@ref)
  * lower and upper bounds, both inclusive
