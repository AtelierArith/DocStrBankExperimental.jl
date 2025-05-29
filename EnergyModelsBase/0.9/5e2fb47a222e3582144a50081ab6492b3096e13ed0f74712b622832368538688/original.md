```
struct EmissionsEnergy{T} <: EmissionsData{T}

EmissionsEnergy(_, _)
EmissionsEnergy(_)
EmissionsEnergy()
```

No capture, no process emissions are present. Does not require `co2_capture` or `emissions` as input, but accepts it and will ignore it, if provided.
