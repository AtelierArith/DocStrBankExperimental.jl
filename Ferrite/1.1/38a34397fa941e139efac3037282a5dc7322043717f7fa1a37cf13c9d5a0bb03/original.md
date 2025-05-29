```
function_value(fe_v::AbstractValues, q_point::Int, u::AbstractVector, [dof_range])
```

Compute the value of the function in a quadrature point. `u` is a vector with values for the degrees of freedom. For a scalar valued function, `u` contains scalars. For a vector valued function, `u` can be a vector of scalars (for use of `VectorValues`) or `u` can be a vector of `Vec`s (for use with ScalarValues).

The value of a scalar valued function is computed as $u(\mathbf{x}) = \sum\limits_{i = 1}^n N_i (\mathbf{x}) u_i$ where $u_i$ are the value of $u$ in the nodes. For a vector valued function the value is calculated as $\mathbf{u}(\mathbf{x}) = \sum\limits_{i = 1}^n N_i (\mathbf{x}) \mathbf{u}_i$ where $\mathbf{u}_i$ are the nodal values of $\mathbf{u}$.
