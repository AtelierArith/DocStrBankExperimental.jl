```julia
motion_subspace(joint, q)

```

Return a basis for the motion subspace of the joint in configuration $q$.

The motion subspace basis is a $6 \times  k$ matrix, where $k$ is the dimension of the velocity vector $v$, that maps $v$ to the twist of the joint's successor with respect to its predecessor. The returned motion subspace is expressed in the frame after the joint, which is attached to the joint's successor.
