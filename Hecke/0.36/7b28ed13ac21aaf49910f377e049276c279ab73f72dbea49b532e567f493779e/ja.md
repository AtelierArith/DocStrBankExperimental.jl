```
norm_change_const(O::AbsSimpleNumFieldOrder) -> (Float64, Float64)
```

返す $(c_1, c_2) \in \mathbf R_{>0}^2$ であり、すべての $x = \sum_{i=1}^d x_i \omega_i \in \mathcal O$ に対して $T_2(x) \leq c_1 \cdot \sum_i^d x_i^2$ および $\sum_i^d x_i^2 \leq c_2 \cdot T_2(x)$ が成り立つ。ここで、$(\omega_i)_i$ は $\mathcal O$ の $\mathbf Z$-基底である。
