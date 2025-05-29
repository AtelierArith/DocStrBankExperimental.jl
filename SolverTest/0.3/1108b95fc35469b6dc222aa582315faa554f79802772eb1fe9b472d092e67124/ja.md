```
multiprecision_nls(solver, problem_type; precisions=[Float16, …, BigFloat])
```

`solver`がさまざまな`precisions`で`problem_type`の問題を解決することをテストします。`problem_type`は次のいずれかです。

  * :unc
  * :bnd
  * :equ
  * :ineq
  * :eqnbnd
  * :gen
