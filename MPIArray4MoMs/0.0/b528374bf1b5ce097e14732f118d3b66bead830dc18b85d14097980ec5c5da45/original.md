```
PatternTransfer{T, I} <: TRANSFER
```

创建特殊用途的 data Transfer, 用于八叉树层内不同 `rank` 间的辐射函数、配置函数的 Pattern 传输数据.

```
parent::MPIArray{T, IA, 3} where {IA}           待传输的 Pattern `MPIArray`。
reqsIndices::I                                  需求的索引
reqsDatas::Dict{Int, SparseMatrixCSC{T, Int}}   用 SparseMatrixCSC 保存 pole 和 θϕ 方向的数据，Dict建保存 cube 数据。
recv_rk2idcs::Dict{Int, I}                      本 `rank` 接收的 `rank` 以及在本地数据中的索引。
send_rk2idcs::Dict{Int, I}                      本 `rank` 发送的 `rank` 以及在本地数据中的索引。
```
