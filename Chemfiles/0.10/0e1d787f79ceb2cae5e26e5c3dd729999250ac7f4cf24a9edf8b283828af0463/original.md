```julia
add_velocities!(frame::Chemfiles.Frame)

```

Add velocities to this `frame`. The storage is initialized with the result of `size(frame)` as the number of atoms. If the frame already has velocities, this does nothing.
