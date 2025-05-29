```
sparse_row_type(a)
```

Return the type of the sparse row type of the given element, element type, parent or parent type $a$.

# Examples

```jldoctest
julia> x = sparse_row(QQ)
Sparse row with positions Int64[] and values QQFieldElem[]

julia> sparse_row_type(QQ) == typeof(x)
true

julia> sparse_row_type(zero(QQ)) == typeof(x)
true

julia> sparse_row_type(typeof(QQ)) == typeof(x)
true

julia> sparse_row_type(typeof(zero(QQ))) == typeof(x)
true
```
