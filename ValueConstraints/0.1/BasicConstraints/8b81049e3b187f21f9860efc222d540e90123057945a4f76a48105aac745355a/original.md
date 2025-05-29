```julia
struct Is{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: The `value` to validate against.

Constrains a value to be some value.
