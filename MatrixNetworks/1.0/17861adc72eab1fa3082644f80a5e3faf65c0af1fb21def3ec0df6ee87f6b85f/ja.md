## MST_PRIM

```
Primのアルゴリズムを使用して最小全域木を計算します。
T = mst_prim_matrix(A) は、非負の辺の重みを持つグラフの全域木に対して
Primのアルゴリズムを使用して最小全域木 T を計算します。

T = mst_prim_matrix(A,false) は、頂点 1 を含む A のコンポーネントの
MST を生成します。 T = mst_prim_matrix(A,0,u) は、頂点 u を含む
コンポーネントの MST を生成します。

(ti,tj,tv,nverts) = mst_prim(A) は、行列から辺を返し、
スパース行列構造に変換しません。 これにより、少し作業が節約され、
辺の重みが 0 の場合に必要です。
```

## 関数

  * (ti,tj,tv,nverts) = mst_prim(A::MatrixNetwork,full::Bool,u::Int64)
  * (ti,tj,tv,nverts) = mst_prim(A::MatrixNetwork)
  * (ti,tj,tv,nverts) = mst_prim{T}(A::SparseMatrixCSC{T,Int64},full::Bool,u::Int64)
  * (ti,tj,tv,nverts) = mst_prim{T}(A::SparseMatrixCSC{T,Int64})
  * T = mst*prim*matrix(A::MatrixNetwork,full::Bool,u::Int64) #出力修飾子
  * T = mst*prim*matrix(A::MatrixNetwork) #出力修飾子
  * T = mst*prim*matrix{T}(A::SparseMatrixCSC{T,Int64},full::Bool,u::Int64) #出力修飾子
  * T = mst*prim*matrix{T}(A::SparseMatrixCSC{T,Int64}) #出力修飾子

## 例

```
A = load_matrix_network("airports")
A = -A #移動時間に変換
A = max.(A,A')
A = sparse(A)
(ti,tj,tv,nverts) = mst_prim(A)
```
