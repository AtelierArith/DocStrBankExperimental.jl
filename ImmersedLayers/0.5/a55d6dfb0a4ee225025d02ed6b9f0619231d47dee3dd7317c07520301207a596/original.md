```
surfaces(sol::ODESolution,sys::ILMSystem,t) -> BodyList
```

Return the list of surfaces (as a `BodyList`) at the time `t`, using the ODE solution array `sol`. If the surfaces are stationary, then this simply returns them and ignores the time argument.
