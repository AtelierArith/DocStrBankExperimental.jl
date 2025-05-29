```julia
struct Minimum{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: The `value` to validate against.

Constrains a value to be larger than or equal to a specified value.
