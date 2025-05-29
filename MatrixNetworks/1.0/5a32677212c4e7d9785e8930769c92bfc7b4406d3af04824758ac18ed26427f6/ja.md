## LARGEST_COMPONENT

```
Aの最大接続成分を返します。
Acc = largest_component(A)は、グラフAの最大接続成分を返します。Aが有向の場合、これは最大強連結成分を返します。

Acc = largest_component(A,true)は、接続性が無向の有向グラフの最大接続部分を返します。アルゴリズム的には、これはAを取り、方向を落とし、最大成分を構成し、元の_有向_ネットワークのこの部分だけを返します。したがって、この場合の出力Accは有向です。

(Acc,p) = largest_component(A)は、Aのどの頂点が選ばれたかを示す論理ベクトルも返します。
```

## Functions

  * (Acc,p) = largest_component{T}(A::SparseMatrixCSC{T,Int64})
  * (Acc,p) = largest_component{T}(A::SparseMatrixCSC{T,Int64},sym::Bool)

## Example

```
A = load_matrix_network("dfs_example")
(Acc,p) = largest_component(A)
```
