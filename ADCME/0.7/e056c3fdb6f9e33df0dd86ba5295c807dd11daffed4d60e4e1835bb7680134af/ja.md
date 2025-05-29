```
pcl_compress(indices::Array{Int64, 2})
```

`compress`のヤコビ行列を計算します。`compress`が以下の変換を行うと仮定します：

```
indices, values (v) --> new_indices, new_values (u)
```

この関数は $J_{ij} = \frac{\partial u_j}{\partial v_i}$ を計算します。
