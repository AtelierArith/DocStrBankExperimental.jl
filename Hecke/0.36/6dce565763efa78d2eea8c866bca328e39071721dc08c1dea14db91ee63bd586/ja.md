```
sparse_matrix_type(a)
```

与えられた要素、要素タイプ、親または親タイプ $a$ のスパース行列タイプのタイプを返します。

# 例

```jldoctest
julia> x = sparse_matrix(QQ)
Sparse 0 x 0 matrix with 0 non-zero entries

julia> sparse_matrix_type(QQ) == typeof(x)
true

julia> sparse_matrix_type(zero(QQ)) == typeof(x)
true

julia> sparse_matrix_type(typeof(QQ)) == typeof(x)
true

julia> sparse_matrix_type(typeof(zero(QQ))) == typeof(x)
true
```
