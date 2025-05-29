```
surfaces(u::ConstrainedSystems.ArrayPartition,sys::ILMSystem,t) -> BodyList
```

Return the list of surfaces (as a `BodyList`) in the solution vector `u`. If the surfaces are stationary, then this simply returns them from `sys` and ignores the time argument.
