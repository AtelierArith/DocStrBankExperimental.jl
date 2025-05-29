```
ConstraintData{C <: AbstractConstraint}
```

A type for storing constraint objects in [`GDPData`](@ref) and any meta-data  they possess.

**Fields**

  * `constraint::C`: The constraint.
  * `name::String`: The name of the proposition.
