```julia
struct ConstraintViolation{S<:ValueConstraints.Interface.AbstractConstraint} <: Exception
```

  * `constraint::ValueConstraints.Interface.AbstractConstraint`: The `constraint` that was violated.
  * `value::Any`: The `value` that violated the constraint.

An `Exception` representing a `value` that failed validation against a `constraint`.

To display descriptive error messages when a `ConstraintViolation` is generated for a specific [`AbstractConstraint`](@ref), define a corresponding `Base.print(io::IO, violation::ConstraintViolation{AbstractConstraint})` method.

Describing errors for [`CompoundConstraint`](@ref)s requires special care, see [`Base.print(io::IO, violation::ConstraintViolation{<:CompoundConstraint})`](@ref) for details.
