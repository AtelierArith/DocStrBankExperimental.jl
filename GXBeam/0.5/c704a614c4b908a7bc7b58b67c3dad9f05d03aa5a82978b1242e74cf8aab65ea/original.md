```
set_internal_forces!([x,] system::Union{StaticSystem,DynamicSystem}, Fi, ielem)
```

Set the state variables in `system` (or in the vector `x`) corresponding to the internal forces of element `ielem` to the provided values.
