## FLOYDWARSHALL

```
フロイド-ワーシャルアルゴリズムを使用してすべての最短経路を計算します。

(D,P) = floydwarshall(A) は、グラフ A のすべてのノード間の最短距離行列を行列 D に返します。 A に負の重みのサイクルがある場合、このアルゴリズムはエラーをスローします。 P は前任者の行列です。
```

## 関数

  * (D,P) = floydwarshall(A::MatrixNetwork)
  * (D,P) = floydwarshall{T}(A::SparseMatrixCSC{T,Int64})

## 例

```
A = load_matrix_network("all_shortest_paths_example")
(D,P) = floydwarshall(A)
```
