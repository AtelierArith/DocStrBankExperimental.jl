```
WaveEquationNonperiodicSemidiscretization(D, left_bc, right_bc)
```

線形波動方程式の半離散化     $\partial_t^2 u(t,x) = \partial_x^2 u(t,x)$。

`D` は二次導関数のSBP演算子であると仮定され、境界条件は `Val(:HomogeneousNeumann)`、`Val(:HomogeneousDirichlet)`、または `Val(:NonReflecting)` であることができます。
