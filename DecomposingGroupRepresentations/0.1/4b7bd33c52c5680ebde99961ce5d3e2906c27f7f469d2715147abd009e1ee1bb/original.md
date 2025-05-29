```
struct MatrixGroupAction{T<:GroupType, F} <: AbstractGroupAction{T, F}
```

Represents a group action of a matrix group on a set of variables.

# Constructors

```julia
MatrixGroupAction(G::S, vectors::AbstractVector{<:AbstractVector{V}}) where {S<:AbstractGroup, V<:Variable}
```

# Examples

```jldoctest
julia> @polyvar x[1:3] y[1:3];

julia> SO3 = LieGroup("SO", 3);

julia> MatrixGroupAction(SO3, [x, y])
MatrixGroupAction of SO(3)
 2 vectors under action: [x₁, x₂, x₃], [y₁, y₂, y₃]
```
