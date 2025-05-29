```
quadratic_matrix_form(f, vars)
```

Extract the linear and quadratic matrices of a system of polynomial equations.

### Input

  * `f`    – vector of polynomials
  * `vars` – vector of variables

### Output

Matrices `F1` and `F2` of size `n × n` and `n × n^2` respectively, such that `F1` contains the linear coefficients of the polynomial vector field `f` and `F2` the quadratic coefficients, which indexing that respects the Kronecker power `vars ⊗ vars`.
