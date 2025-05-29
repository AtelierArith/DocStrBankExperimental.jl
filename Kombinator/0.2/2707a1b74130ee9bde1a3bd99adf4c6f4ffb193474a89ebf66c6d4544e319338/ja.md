```
struct MinimumBudget{CI <: CombinatorialInstance, T <: Real}
```

最小予算制約を実装します。つまり、使用しなければならないリソースの最小量です。

$$
\sum_i x_i \times \mathtt{weights}_i \geq \mathtt{min\_budget}
$$
