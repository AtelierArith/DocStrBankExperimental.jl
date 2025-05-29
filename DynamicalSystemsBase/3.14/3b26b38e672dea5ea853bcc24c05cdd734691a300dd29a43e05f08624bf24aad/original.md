```
set_state!(ds::DynamicalSystem, u::AbstractArray{<:Real})
```

Set the state of `ds` to `u`, which must match dimensionality with that of `ds`. Also ensure that the change is notified to whatever integration protocol is used.
