```
openblas_getaffinity(; threadid, convert = true)
```

指定された `threadid`（通常は `1:BLAS.get_num_threads()`）を持つOpenBLASスレッドのアフィニティを照会します。デフォルトでは、マスクを表すベクトルが返されます。`convert=false`の場合は、代わりに `Ccpu_set_t` が返されます。
