```
GrB_error()
```

各GraphBLASメソッドおよび操作は、`GrB_Info`エラーコードを返します。`GrB_error`は、最後のエラーに関する追加情報を返します。

# 例

```jldoctest
julia> using GraphBLASInterface, SuiteSparseGraphBLAS

julia> GrB_init(GrB_NONBLOCKING)
GrB_SUCCESS::GrB_Info = 0

julia> GrB_init(GrB_NONBLOCKING)
GrB_INVALID_VALUE::GrB_Info = 5

julia> GrB_error()
GraphBLASエラー: GrB_INVALID_VALUE
関数: GrB_init (モード)
GrB_initは二度呼び出してはいけません
```
