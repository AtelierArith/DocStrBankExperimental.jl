```
distinct(x, y)
distinct(zs::Array{AbstractExpr})
```

Returns the SMT-LIB `distinct` operator. `distinct(x, y)` is semantically equal to `x != y` or `not(x == y)`. The syntax `distinct(exprs)` where `exprs` is an array of expressions is shorthand for "every element of zs is unique". Thus,

```julia @satvariable(a[1:3], Int)

# this statement is true

isequal(     distinct(a)     and(distinct(a[1], a[2]), distinct(a[1], a[3]), distinct(a[2], a[3]))     ) ````
