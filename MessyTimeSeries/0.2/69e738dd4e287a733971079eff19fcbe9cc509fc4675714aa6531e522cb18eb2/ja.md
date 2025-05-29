```
is_vector_in_matrix(vect::IntVector, matr::IntMatrix)
is_vector_in_matrix(vect::FloatVector, matr::FloatMatrix)
```

ベクトル `vect` が行列 `matr` に含まれているかどうかを確認します。

# 例

julia> is*vector*in_matrix([1; 2], [1 2; 2 3]) true
