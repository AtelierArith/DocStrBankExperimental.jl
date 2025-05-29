```julia
fixed_transform(mechanism, from, to)

```

Return the transform from `CartesianFrame3D` `from` to `to`, both of which are rigidly attached to the same `RigidBody`.

Note: this function is linear in the number of bodies and is not meant to be called in tight loops.
