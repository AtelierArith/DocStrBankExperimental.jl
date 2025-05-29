```
function_gradient(iv::InterfaceValues, q_point::Int, u; here::Bool)
function_gradient(iv::InterfaceValues, q_point::Int, u, dof_range_here, dof_range_there; here::Bool)
```

Compute the gradient of the function in a quadrature point. `u` is a vector of scalar values for the degrees of freedom. This function can be used with a single `u` vector containing the dofs of both elements of the interface or two vectors (`u_here` and `u_there`) which contain the dofs of each cell of the interface respectively.

`here` determines which element to use for calculating function value. `true` uses the value on the first element's side of the interface, while `false` uses the value on the second element's side.

The gradient of a scalar function or a vector valued function with use of `VectorValues` is computed as $\mathbf{\nabla} u(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{\nabla} N_i (\mathbf{x}) u_i$ or $\mathbf{\nabla} u(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{\nabla} \mathbf{N}_i (\mathbf{x}) u_i$ respectively, where $u_i$ are the nodal values of the function. For a vector valued function with use of `ScalarValues` the gradient is computed as $\mathbf{\nabla} \mathbf{u}(\mathbf{x}) = \sum\limits_{i = 1}^n \mathbf{u}_i \otimes \mathbf{\nabla} N_i (\mathbf{x})$ where $\mathbf{u}_i$ are the nodal values of $\mathbf{u}$.
