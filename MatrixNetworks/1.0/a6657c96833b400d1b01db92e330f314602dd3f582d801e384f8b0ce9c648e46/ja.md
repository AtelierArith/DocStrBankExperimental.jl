## BFS

```
幅優先探索の距離を計算し、距離(d)、発見時間(dt)、前駆体配列(pred)をタプル(d,dt,pred)で返します。
pred[i] = 0 は、頂点 i が u から到達できない成分にある場合、かつ i != u の場合です。
探索は、ターゲット頂点に到達すると停止します。
```

## 関数

  * (d,dt,pred) = bfs(A::MatrixNetwork,u::Int64,target::Int64)
  * (d,dt,pred) = bfs{T}(A::SparseMatrixCSC{T,Int64}),u::Int64,target::Int64)
  * (d,dt,pred) = bfs(ei::Vector{Int64},ej::Vector{Int64},u::Int64,target::Int64)

ターゲットが指定されていない場合、0 に割り当てられます。

## 例

```
A = load_matrix_network("bfs_example")
(d,dt,pred) = bfs(A,1)
```
