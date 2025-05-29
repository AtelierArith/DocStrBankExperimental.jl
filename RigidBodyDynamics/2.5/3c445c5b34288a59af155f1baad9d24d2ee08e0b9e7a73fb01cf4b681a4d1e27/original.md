```julia
momentum_matrix!(mat, state, transformfun)

```

Compute the momentum matrix $A(q)$ of the `Mechanism` in the given state.

The momentum matrix maps the `Mechanism`'s joint velocity vector $v$ to its total momentum.

See also [`MomentumMatrix`](@ref).

The `out` argument must be a mutable `MomentumMatrix` with as many columns as the dimension of the `Mechanism`'s joint velocity vector $v$.

`transformfun` is a callable that may be used to transform the individual momentum matrix blocks associated with each of the joints to the frame in which `out` is expressed.

This method does its computation in place, performing no dynamic memory allocation.
