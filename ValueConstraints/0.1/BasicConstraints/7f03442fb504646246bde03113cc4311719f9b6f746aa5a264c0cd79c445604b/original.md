```julia
struct ExclusiveMinimum{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: The `value` to validate against.

Constrains a value to be larger than a specified value.
