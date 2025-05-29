```
savetime!(model::SimModel) -> t
```

Set `model.t` to `time()`  and return the value.

Used in conjunction with [`periodsleep`](@ref) for simple soft real-time simulations. Call this function before any other in the simulation loop.
