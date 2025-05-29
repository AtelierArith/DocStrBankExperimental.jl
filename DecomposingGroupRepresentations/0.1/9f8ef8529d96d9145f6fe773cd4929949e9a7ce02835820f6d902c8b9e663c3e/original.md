```
GroupRepresentation <: AbstractGroupRepresentation
```

Represents a group representation. Consists of a group action and a vector space.

# Constructors

```julia
GroupRepresentation(a::AbstractGroupAction, V::AbstractSpace)
```

# Examples

```jldoctest
julia> @polyvar x[1:3];

julia> SO3 = LieGroup("SO", 3);

julia> a = MatrixGroupAction(SO3, [x]);

julia> V = FixedDegreePolynomials(x, 2);

julia> ρ = GroupRepresentation(a, V)
GroupRepresentation of SO(3) on 6-dimensional vector space
 Lie group: SO(3)

julia> dim(ρ)
6

julia> group(ρ)
LieGroup SO(3)
 number type (or field): ComplexF64
 weight type: Int64
 Lie algebra properties:
  dimension: 3
  rank (dimension of Cartan subalgebra): 1
```
