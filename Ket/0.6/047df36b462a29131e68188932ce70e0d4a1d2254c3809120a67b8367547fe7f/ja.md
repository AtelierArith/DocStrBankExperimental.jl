```
permute_systems(X::AbstractMatrix, perm::AbstractVector, dims::AbstractVector = _equal_sizes(X))
```

正方行列 `X` の部分系の順序を、置換 `perm` に従って、次元 `dims` の正方部分系で構成されるように入れ替えます。引数 `dims` が省略された場合、同じサイズの2つの部分系が仮定されます。
