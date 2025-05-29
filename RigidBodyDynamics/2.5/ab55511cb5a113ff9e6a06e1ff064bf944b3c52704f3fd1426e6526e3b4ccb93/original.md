```julia
mass_matrix(state)

```

Compute the joint-space mass matrix (also known as the inertia matrix) of the `Mechanism` in the given state, i.e., the matrix $M(q)$ in the unconstrained joint-space equations of motion

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau
$$

This method implements the composite rigid body algorithm.
