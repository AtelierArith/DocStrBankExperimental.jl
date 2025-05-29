```
var_coordinates(data::DataMatrix)
```

変数の座標を持つ行列を返します。双対表現（例：SVD/PCA）を持つDataMatrixにのみ利用可能です。

`SVD`（PCA）の場合、`var_coordinates`は主成分を単位ベクトルとして返します。
