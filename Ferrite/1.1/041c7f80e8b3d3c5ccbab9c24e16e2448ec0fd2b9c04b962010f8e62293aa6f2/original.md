```
function_gradient(fe_v::AbstractValues{dim}, q_point::Int, u::AbstractVector, [dof_range])
```

Compute the gradient of the function in a quadrature point. `u` is a vector with values for the degrees of freedom. For a scalar valued function, `u` contains scalars. For a vector valued function, `u` can be a vector of scalars (for use of `VectorValues`) or `u` can be a vector of `Vec`s (for use with ScalarValues).

The gradient of a scalar function or a vector valued function with use of `VectorValues` is computed as $\mathbf{\nabla} u(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{\nabla} N_i (\mathbf{x}) u_i$ or $\mathbf{\nabla} u(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{\nabla} \mathbf{N}_i (\mathbf{x}) u_i$ respectively, where $u_i$ are the nodal values of the function. For a vector valued function with use of `ScalarValues` the gradient is computed as $\mathbf{\nabla} \mathbf{u}(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{u}_i \otimes \mathbf{\nabla} N_i (\mathbf{x})$ where $\mathbf{u}_i$ are the nodal values of $\mathbf{u}$.
