```
norm_change_const(O::AbsSimpleNumFieldOrder) -> (Float64, Float64)
```

Returns $(c_1, c_2) \in \mathbf R_{>0}^2$ such that for all $x = \sum_{i=1}^d x_i \omega_i \in \mathcal O$ we have $T_2(x) \leq c_1 \cdot \sum_i^d x_i^2$ and $\sum_i^d x_i^2 \leq c_2 \cdot T_2(x)$, where $(\omega_i)_i$ is the $\mathbf Z$-basis of $\mathcal O$.
