```julia
struct MultipleOf{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: The `value` to validate against.

Constrains a value to be a multiple of a specified value.
