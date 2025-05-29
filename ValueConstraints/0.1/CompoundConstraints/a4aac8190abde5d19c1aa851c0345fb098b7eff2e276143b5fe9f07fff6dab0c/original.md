```julia
struct AtMost{S, T<:Tuple{ValueConstraints.Interface.AbstractConstraint, Vararg{ValueConstraints.Interface.AbstractConstraint}}} <: ValueConstraints.CompoundConstraints.CompoundConstraint
```

  * `constraints::Tuple{ValueConstraints.Interface.AbstractConstraint, Vararg{ValueConstraints.Interface.AbstractConstraint}}`: The collection of `AbstractConstraint`s that is to be evaluated.

A compound constraint requiring at most `S` of its wrapped `constraints` to be valid.

All wrapped `constraints` are 'eagerly' evaluated, i.e. even if too many `constraints` have already succeeded all others are still evaluated as well.
