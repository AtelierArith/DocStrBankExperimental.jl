```
function_curl(fe_v::AbstractValues, q_point::Int, u::AbstractVector, [dof_range])
```

四分点におけるベクトル値関数のカールを計算します。

四分点 $\mathbf{x}_q)$ におけるベクトル値関数のカールは、$\mathbf{\nabla} \times \mathbf{u}(\mathbf{x_q}) = \sum\limits_{i = 1}^n \mathbf{\nabla} N_i \times (\mathbf{x_q}) \cdot \mathbf{u}_i$ として計算されます。ここで、$\mathbf{u}_i$ は関数のノード値です。
