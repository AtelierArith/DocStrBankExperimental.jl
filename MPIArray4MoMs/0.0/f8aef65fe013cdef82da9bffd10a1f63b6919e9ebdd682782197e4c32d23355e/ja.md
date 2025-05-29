ArrayTransfer{T, N, I} <: TRANSFER

独立于 `MPIArray` 的数据传输器。

```
parent::MPIArray{T, IA, N} where {IA}                       待传输的 Pattern `MPIArray`。
reqsIndices::NTuple{N, Union{UnitRange{Int}, Vector{Int}}}  需求的索引
reqsDatas::Dict{Int, ArrayChunk{T, N}}                      用 ArrayChunk 保存 pole 和 θϕ 方向的数据，Dict建保存 cube 数据。
recv_rk2idcs::Dict{Int, I}                                  本 `rank` 接收的 `rank` 以及在本地数据中的索引。
send_rk2idcs::Dict{Int, I}                                  本 `rank` 发送的 `rank` 以及在本地数据中的索引。
```
