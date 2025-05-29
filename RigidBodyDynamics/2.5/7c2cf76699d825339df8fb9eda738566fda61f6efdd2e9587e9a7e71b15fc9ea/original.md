```julia
momentum_matrix!(out, state)

```

Compute the momentum matrix $A(q)$ of the `Mechanism` in the given state.

The momentum matrix maps the `Mechanism`'s joint velocity vector $v$ to its total momentum.

See also [`MomentumMatrix`](@ref).

The `out` argument must be a mutable `MomentumMatrix` with as many columns as the dimension of the `Mechanism`'s joint velocity vector $v$.

See [`momentum_matrix!(out, state, root_to_desired)`](@ref). Uses `state` to compute the transform from the `Mechanism`'s root frame to the frame in which `out` is expressed.

This method does its computation in place, performing no dynamic memory allocation.
