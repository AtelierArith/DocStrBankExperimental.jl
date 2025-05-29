```julia
struct Maximum{S} <: ValueConstraints.Interface.AbstractConstraint
```

  * `value::Any`: The `value` to validate against.

Constrains a value to be less than or equal to a specified value.
