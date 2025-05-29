# `is_empty`

グラフが空のグラフであれば true を返し、それ以外の場合は false を返します。

## 関数

-`is_empty(A::MatrixNetwork)`

## 例

```
is_empty(MatrixNetwork(Int[],Int[],0))
is_empty(erdos_renyi_undirected(0,0))
```
