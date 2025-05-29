```
SFCC <: FreezeCurve
```

Base type for a soil freeze characteristic curve (SFCC) function. Subtypes should be callable structs that implement the freeze curve and contain any necessary additional constants or configuration options. User-specified parameters can either be supplied in the struct or declared as model parameters via the `variables` method.
