```
make_mat(elements::Vector, rates::Vector, nT::Int)
```

nT x nT の疎行列 T を返します。

# 説明

この関数は、提供された要素とレートに従って設定された nT x nT の疎行列 T を返します。

# 引数

  * `elements::Vector`: 行列に設定する要素のベクトル。
  * `rates::Vector`: 要素に対応するレートのベクトル。
  * `nT::Int`: 行列のサイズ (nT x nT)。

# 返り値

  * `SparseMatrixCSC`: 作成された疎行列 T。
