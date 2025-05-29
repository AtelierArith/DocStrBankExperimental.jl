```
struct MinimumBudget{CI <: CombinatorialInstance, T <: Real}
```

Implement a minimum-budget constraint, i.e. a minimum quantity of a resource  that must be used.

$\sum_i x_i \times \mathtt{weights}_i \geq \mathtt{min\_budget}$
