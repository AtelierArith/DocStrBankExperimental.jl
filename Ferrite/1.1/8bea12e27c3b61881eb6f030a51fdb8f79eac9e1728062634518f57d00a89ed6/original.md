```
function_value(iv::InterfaceValues, q_point::Int, u; here::Bool)
function_value(iv::InterfaceValues, q_point::Int, u, dof_range_here, dof_range_there; here::Bool)
```

Compute the value of the function in quadrature point `q_point` on the "here" (`here=true`) or "there" (`here=false`) side of the interface. `u_here` and `u_there` are the values of the degrees of freedom for the respective element.

`u` is a vector of scalar values for the degrees of freedom. This function can be used with a single `u` vector containing the dofs of both elements of the interface or two vectors (`u_here` and `u_there`) which contain the dofs of each cell of the interface respectively.

`here` determines which element to use for calculating function value. `true` uses the value on the first element's side of the interface, while `false` uses the value on the second element's side.

The value of a scalar valued function is computed as $u(\mathbf{x}) = \sum\limits_{i = 1}^n N_i (\mathbf{x}) u_i$ where $u_i$ are the value of $u$ in the nodes. For a vector valued function the value is calculated as $\mathbf{u}(\mathbf{x}) = \sum\limits_{i = 1}^n N_i (\mathbf{x}) \mathbf{u}_i$ where $\mathbf{u}_i$ are the nodal values of $\mathbf{u}$.
