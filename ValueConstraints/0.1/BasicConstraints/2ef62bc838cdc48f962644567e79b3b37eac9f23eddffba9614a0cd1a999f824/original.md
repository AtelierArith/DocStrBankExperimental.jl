```julia
struct ExclusiveMaximum{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: The `value` to validate against.

Constrains a value to be less than a specified value.
