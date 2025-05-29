```julia
inverse_dynamics!(
    torquesout,
    jointwrenchesout,
    accelerations,
    state,
    v̇
)
inverse_dynamics!(
    torquesout,
    jointwrenchesout,
    accelerations,
    state,
    v̇,
    externalwrenches
)

```

Do inverse dynamics, i.e. compute $\tau$ in the unconstrained joint-space equations of motion

$$
M(q) \dot{v} + c(q, v, w_\text{ext}) = \tau
$$

given joint configuration vector $q$, joint velocity vector $v$, joint acceleration vector $\dot{v}$ and (optionally) external wrenches $w_\text{ext}$.

The `externalwrenches` argument can be used to specify additional wrenches that act on the `Mechanism`'s bodies.

This method implements the recursive Newton-Euler algorithm.

Currently doesn't support `Mechanism`s with cycles.

This method does its computation in place, performing no dynamic memory allocation.
