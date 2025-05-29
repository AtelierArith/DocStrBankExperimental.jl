```
normalize_indices!(expr_tree, vector_indices::Vector{Int})
```

`expr_tree`の変数のインデックスを`vector_indices`で指定された順序に従うように変更します。これは、要素関数の式木を定義するために`get_elemental_variables`と組み合わせて使用されます。`expr_tree`は`Expr`、`Type_expr_tree`、または`Complete_expr_tree`のいずれかである可能性があります。

例:

```julia
julia> normalize_indices!(:(x[4] + x[5]), [4,5])
:(x[1] + x[2])
```
