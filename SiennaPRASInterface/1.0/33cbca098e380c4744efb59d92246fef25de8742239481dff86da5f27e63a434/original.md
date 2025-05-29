```
StoragePRAS <: AbstractRAFormulation
```

Objects in Sienna that behave like storage are mapped to storage in PRAS.

Subtypes must provide [`assign_to_stor_matrices!`](@ref) function.
