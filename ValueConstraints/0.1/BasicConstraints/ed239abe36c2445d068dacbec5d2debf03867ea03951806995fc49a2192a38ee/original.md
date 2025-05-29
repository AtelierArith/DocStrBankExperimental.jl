```julia
struct Not{S<:ValueConstraints.Interface.AbstractConstraint} <: ValueConstraints.Interface.AbstractConstraint
```

  * `constraint::ValueConstraints.Interface.AbstractConstraint`: The `constraint` to invert.

Represents the inversion of a `constraint`.
