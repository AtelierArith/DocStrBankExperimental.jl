```
tightlimits!(la::LAxis, sides::Union{Left, Right, Bottom, Top}...)
```

Sets the autolimit margins to zero on all given sides.

Example:

```
tightlimits!(laxis, Bottom())
```
