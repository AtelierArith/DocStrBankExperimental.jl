```
sparse_matrix_type(a)
```

Return the type of the sparse matrix type of the given element, element type, parent or parent type $a$.

# Examples

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
