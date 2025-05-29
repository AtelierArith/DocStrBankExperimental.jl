```
function_curl(fe_v::AbstractValues, q_point::Int, u::AbstractVector, [dof_range])
```

Compute the curl of the vector valued function in a quadrature point.

The curl of a vector valued functions in the quadrature point $\mathbf{x}_q)$ is computed as $\mathbf{\nabla} \times \mathbf{u}(\mathbf{x_q}) = \sum\limits_{i = 1}^n \mathbf{\nabla} N_i \times (\mathbf{x_q}) \cdot \mathbf{u}_i$ where $\mathbf{u}_i$ are the nodal values of the function.
