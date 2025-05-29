```
DisabledControl()
```

Control that disables a well. If a well is disabled, it is disconnected from the surface network and no flow occurs between the well and the top side. Mass transfer can still occur inside the well, and between the well and the reservoir unless perforations are also closed by a [`PerforationMask`](@ref).

See also [`ProducerControl`](@ref), [`InjectorControl`](@ref).
