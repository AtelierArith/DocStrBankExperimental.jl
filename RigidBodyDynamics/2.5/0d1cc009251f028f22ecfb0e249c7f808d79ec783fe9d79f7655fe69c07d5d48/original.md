```julia
Mechanism(root_body; gravity)

```

Create a new `Mechanism` containing only a root body, to which other bodies can be attached with joints.

The `gravity` keyword argument can be used to set the gravitational acceleration (a 3-vector expressed in the `Mechanism`'s root frame). Default: `[0.0, 0.0, -9.81]`.
