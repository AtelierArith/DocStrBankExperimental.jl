## COSINEKNN

```
Aの頂点または二部グラフAの上半分の間のk近傍類似度メトリックを計算します。
```

## 関数

  * S = cosineknn{T}(A::SparseMatrixCSC{T,Int64},K::Int64)
  * S = cosineknn(A::MatrixNetwork,K::Int64)

## 例

```
A = load_matrix_network("bfs_example")
S = cosineknn(A,2)
```
