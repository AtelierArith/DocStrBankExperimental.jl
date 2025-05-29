```
get_solution(sol, op::QTerm)
get_solution(sol, op::QNumber)
```

ODEまたはSteadyStateProblemの解`sol`における演算子式`op`の平均の結果を返します。これは`sol[op]`に似ています。また、`sol[op]`では不可能な演算子の線形結合にも使用できます。
