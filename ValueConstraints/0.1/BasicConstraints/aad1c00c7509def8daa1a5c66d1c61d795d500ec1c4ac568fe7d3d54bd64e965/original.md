```julia
struct Always <: ValueConstraints.Interface.AbstractConstraint
```

Represents a constraint that is valid no matter which `value` is validated against it.

Useful for shortcircuiting code, e.g. in tests, that requires validation of a constraint where it is not straightforward to make less trivial constraints pass.
