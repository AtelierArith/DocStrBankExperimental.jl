```
DiffEqArrayOperator(A[; update_func])
```

AbstractMatrixによって与えられる時間依存の線形演算子を表します。更新関数は`update_coefficients!`によって呼び出され、次のシグネチャを持つと仮定されます。

```
update_func(A::AbstractMatrix,u,p,t) -> [Aを修正]
```
