```julia
write_urdf(io, mechanism; robot_name, include_root)

```

Write a URDF representation of `mechanism` to the stream `io` (a `Base.IO`).

Optionally, the `robot_name` keyword argument can be used to specify the robot's name.
