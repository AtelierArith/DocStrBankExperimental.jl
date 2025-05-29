```julia
point_jacobian!(out, state, path, point)

```

Compute the Jacobian mapping the `Mechanism`'s joint velocity vector $v$ to the velocity of a point fixed to the target of the joint path (the body succeeding the last joint in the path) with respect to the source of the joint path (the body preceding the first joint in the path).

Uses `state` to compute the transform from the `Mechanism`'s root frame to the frame in which `out` is expressed if necessary.

This method does its computation in place, performing no dynamic memory allocation.
