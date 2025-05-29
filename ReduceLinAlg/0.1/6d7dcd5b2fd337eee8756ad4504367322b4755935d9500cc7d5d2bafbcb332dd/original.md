```
hessian(expr,var_list::Vector)
```

Computes the Hessian matrix of `expr` with respect to the variables in `var_list`.

This is an n×n matrix where n is the number of variables and the (i,j)th entry is `df(expr,var_list[i],var_list[j])`.
