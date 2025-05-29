```julia
mutable struct Mechanism{T}
```

A `Mechanism` represents an interconnection of rigid bodies and joints. `Mechanism`s store the joint layout and inertia parameters, but no state-dependent information.
