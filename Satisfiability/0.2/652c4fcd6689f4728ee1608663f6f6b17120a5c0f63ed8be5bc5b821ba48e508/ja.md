```
distinct(x, y)
distinct(zs::Array{AbstractExpr})
```

SMT-LIBの`distinct`演算子を返します。`distinct(x, y)`は意味的に`x != y`または`not(x == y)`と等しいです。`distinct(exprs)`という構文は、`exprs`が式の配列である場合、「zsのすべての要素がユニークである」という短縮形です。したがって、

```julia @satvariable(a[1:3], Int)

# この文は真です

isequal(     distinct(a)     and(distinct(a[1], a[2]), distinct(a[1], a[3]), distinct(a[2], a[3]))     ) ````
