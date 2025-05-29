```
LieGroup{F} <: AbstractGroup{Lie, F}
```

Describes a matrix Lie group.

# Constructors

```julia
LieGroup(type::String, size::Int)
```

Supported Lie group types: SO (special orthogonal).

# Examples

```jldoctest
julia> SO3 = LieGroup("SO", 3)
LieGroup SO(3)
 number type (or field): ComplexF64
 weight type: Int64
 Lie algebra properties:
  dimension: 3
  rank (dimension of Cartan subalgebra): 1
```
