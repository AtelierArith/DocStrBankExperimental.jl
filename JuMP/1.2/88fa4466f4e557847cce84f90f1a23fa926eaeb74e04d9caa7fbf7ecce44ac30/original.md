```
struct VectorConstraint
```

The data for a vector constraint. The `func` field contains a JuMP object representing the function and the `set` field contains the MOI set. The `shape` field contains an [`AbstractShape`](@ref) matching the form in which the constraint was constructed (e.g., by using matrices or flat vectors). See also the [documentation](@ref Constraints) on JuMP's representation of constraints.
