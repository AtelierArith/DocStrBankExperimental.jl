## CORENUMS

```
グラフの各頂点のコア数を計算し、グラフ A の各頂点のコア数と頂点の削除順序をタプル (d,rt) で返します。この関数は有向グラフで動作しますが、入次数コア数を返します。出次数コア数を取得するには corenums(A') を呼び出してください。
```

## Functions

  * (d,rt) = corenums(A::MatrixNetwork)
  * (d,rt) = corenums{T}(A::SparseMatrixCSC{T,Int64})
  * (d,rt) = corenums(ei::Vector{Int64},ej::Vector{Int64})

## Example

```
A = load_matrix_network("cores_example")
(d,rt) = corenums(A)
```
