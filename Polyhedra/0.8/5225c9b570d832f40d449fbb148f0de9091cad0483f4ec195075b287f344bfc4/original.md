```
vrep(lines::LineIt, rays::RayIt; d::FullDim)
```

Creates a V-representation for the polyhedral cone of full dimension `d` equal to the conic hull of the lines `lines` and rays `rays`.

### Examples

```julia
vrep([Line([0, 1])], [Ray([1, 0])])
```

creates a V-representation for the halfspace $x_1 \ge 0$.
