## DFS

```
深さ優先探索の距離を計算し、距離 (d)、発見時間 (dt)、終了時間 (ft)、および前任者配列 (pred) をタプル (d,dt,ft, pred) で返します。

pred[i] = 0 は、頂点 i が u から到達できない成分にある場合、かつ i != u の場合です。
```

## 関数

  * (d,dt,ft,pred) = dfs(A::MatrixNetwork,u::Int64,full::Int64,target::Int64)
  * (d,dt,ft,pred) = dfs(A::MatrixNetwork,u::Int64)
  * (d,dt,ft,pred) = dfs{T}(A::SparseMatrixCSC{T,Int64},u::Int64,full::Int64,target::Int64)
  * (d,dt,ft,pred) = dfs{T}(A::SparseMatrixCSC{T,Int64},u::Int64)
  * (d,dt,ft,pred) = dfs(ei::Vector{Int64},ej::Vector{Int64},u::Int64,full::Int64,target::Int64)
  * (d,dt,ft,pred) = dfs(ei::Vector{Int64},ej::Vector{Int64},u::Int64)

## 例

```
A = load_matrix_network("dfs_example")
(d,dt,ft,pred)  = dfs(A,1)
```
