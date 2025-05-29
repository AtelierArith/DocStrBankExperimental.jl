```julia
struct Interaction <: OpenQuantumBase.AbstractInteraction
```

An object to hold coupling operator and the corresponding bath object.

  * `coupling`: system operator
  * `bath`: bath coupling to the system operator
