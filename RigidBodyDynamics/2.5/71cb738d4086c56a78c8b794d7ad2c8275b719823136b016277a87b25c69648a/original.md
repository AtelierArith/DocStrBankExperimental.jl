```julia
mass_matrix!(M, state)

```

Compute the joint-space mass matrix (also known as the inertia matrix) of the `Mechanism` in the given state, i.e., the matrix $M(q)$ in the unconstrained joint-space equations of motion

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau
$$

This method implements the composite rigid body algorithm.

This method does its computation in place, performing no dynamic memory allocation.

The `out` argument must be an $n_v \times n_v$ lower triangular `Symmetric` matrix, where $n_v$ is the dimension of the `Mechanism`'s joint velocity vector $v$.
