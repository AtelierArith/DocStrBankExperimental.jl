```julia
struct IsA{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: The `value` to validate against.

Constrains a value to be of a specific type.
