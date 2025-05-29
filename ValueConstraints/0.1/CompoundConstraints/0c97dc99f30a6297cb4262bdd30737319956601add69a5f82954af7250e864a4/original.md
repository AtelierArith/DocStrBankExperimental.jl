```julia
All(
    constraints::ValueConstraints.Interface.AbstractConstraint...
) -> ValueConstraints.BasicConstraints.Always

```

A compound constraint requiring all `constraints` to be valid.

This is a shorthand for instantiating an [`Exactly`](@ref) constraint for the amount of passed `constraints`.

All wrapped constraints are 'eagerly' evaluated, i.e. even if one of the `constraints` fails, all others are still evaluated as well.
