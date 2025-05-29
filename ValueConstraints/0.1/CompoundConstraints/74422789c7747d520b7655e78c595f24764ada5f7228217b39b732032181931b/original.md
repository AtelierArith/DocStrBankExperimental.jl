```julia
None(
    constraints::ValueConstraints.Interface.AbstractConstraint...
) -> ValueConstraints.BasicConstraints.Always

```

A compound constraint requiring none of the `constraints` to be valid or, phrased differently, requiring all of the `constraints` to be invalid.

This is a shorthand for instantiating an [`Exactly`](@ref) constraint requiring `0` `constraints` to be valid.

All wrapped constraints are 'eagerly' evaluated, i.e. even if one of the `constraints` succeeds, all others are still evaluated as well.
