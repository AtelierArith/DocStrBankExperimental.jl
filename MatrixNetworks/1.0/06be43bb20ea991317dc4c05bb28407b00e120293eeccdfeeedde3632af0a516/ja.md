## CLUSTERCOEFFS

```
グラフの無向クラスタリング係数を計算します。 clustercoeffs(A) は、対称隣接行列 A で表されるグラフから正規化された重み付きクラスタリング係数を計算します。 clustercoeffs(A,weighted,normalized) は、計算が重み付けされるべきかどうか、または正規化されるべきかどうかを示すブール値 weighted と normalized を持ちます。
```

## Functions

  * cc = clustercoeffs(A::MatrixNetwork,weighted::Bool,normalized::Bool)
  * cc = clustercoeffs{T}(A::SparseMatrixCSC{T,Int64},weighted::Bool,normalized::Bool)

weighted と normalized が指定されていない場合、それらは true として理解されます。

## Example

```
A = load_matrix_network("clique-10")    
cc = clustercoeffs(MatrixNetwork(A))    
```
