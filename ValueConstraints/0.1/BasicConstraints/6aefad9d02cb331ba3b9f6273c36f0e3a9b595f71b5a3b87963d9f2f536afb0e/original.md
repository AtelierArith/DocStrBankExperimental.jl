```julia
struct Never <: ValueConstraints.Interface.AbstractConstraint
```

Represents a constraint that is *not* valid no matter which `value` is validated against it.
