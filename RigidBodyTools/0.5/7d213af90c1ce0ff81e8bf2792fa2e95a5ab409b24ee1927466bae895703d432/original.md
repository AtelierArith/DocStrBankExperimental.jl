```
motion_subspace(j::Joint)
```

Return the `6 x ndof` (3d) or `3 x ndof` (2d) matrix providing the mapping from joint dof velocities to the full Plucker velocity vector of the joint. This matrix represents the subspace of free motion in the full space. It is orthogonal to the constrained subspace.
