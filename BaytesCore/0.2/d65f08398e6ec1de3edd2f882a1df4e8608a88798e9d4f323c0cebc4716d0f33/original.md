```julia
mutable struct Updater
```

Mutable struct to store update information that can be stored and updated in immutable structs. Contains boolean if updated is needed. Note that a UpdateBool field cannot be stored and updated as a concrete type here.

# Fields

  * `current::Bool`: Boolean of whether update has to be applied
