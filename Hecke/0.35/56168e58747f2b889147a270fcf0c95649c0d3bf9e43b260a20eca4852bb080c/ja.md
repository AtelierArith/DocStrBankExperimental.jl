```
sparse_row_type(a)
```

与えられた要素、要素の型、親または親の型 $a$ のスパース行型の型を返します。

# 例

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
