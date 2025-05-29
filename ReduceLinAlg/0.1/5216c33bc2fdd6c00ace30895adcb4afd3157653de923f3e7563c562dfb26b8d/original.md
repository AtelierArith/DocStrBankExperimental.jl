```
mat_jacobian(expr_list::Vector,var_list::Vector)
```

Computes the Jacobian matrix of `expr_list` with respect to `var_list`.

This is a matrix whose (i,j)th entry is `df(expr_list[i],var_list[j])`. The matrix is n×m where n is the number of variables and m is the number of expressions.
