```
tightlimits!(la::Axis, sides::Union{Left, Right, Bottom, Top}...)
```

Sets the autolimit margins to zero on all given sides.

Example:

```julia
tightlimits!(laxis, Bottom())
```
