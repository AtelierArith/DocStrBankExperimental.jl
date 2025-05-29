```
CriticalStretch
```

A damage model based on the stretch of the bond. The bond is considered to be broken if the stretch exceeds a critical value. The critical value can be defined via the fracture energy `Gc` or the critical stretch `εc` using the [`material!`](@ref) function. The damage model is defined globally for the whole body as part of the material.
