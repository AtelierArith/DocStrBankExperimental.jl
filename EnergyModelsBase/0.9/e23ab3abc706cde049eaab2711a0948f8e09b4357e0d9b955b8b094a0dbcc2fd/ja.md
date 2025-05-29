```
struct StorCap <: AbstractStorageParameters
```

容量のみを含むストレージパラメータタイプです。これは、[`Storage`](@ref)の使用や、設置された容量が目的関数に直接影響を与えないことを意味します。

# フィールド

  * **`capacity::TimeProfile`** は設置された容量です。
