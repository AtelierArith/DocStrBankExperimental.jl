```
function_symmetric_gradient(fe_v::AbstractValues, q_point::Int, u::AbstractVector, [dof_range])
```

Compute the symmetric gradient of the function, see [`function_gradient`](@ref). Return a `SymmetricTensor`.

The symmetric gradient of a scalar function is computed as $\left[ \mathbf{\nabla}  \mathbf{u}(\mathbf{x_q}) \right]^\text{sym} =  \sum\limits_{i = 1}^n  \frac{1}{2} \left[ \mathbf{\nabla} N_i (\mathbf{x}_q) \otimes \mathbf{u}_i + \mathbf{u}_i  \otimes  \mathbf{\nabla} N_i (\mathbf{x}_q) \right]$ where $\mathbf{u}_i$ are the nodal values of the function.
