```julia
DiscreteUpdate(t; dt)

```

Represents a discrete update (shift) operator with the semantics

```
DiscreteUpdate(t; dt=0.01)(y) ~ y(t+dt)
```

# Examples

```jldoctest
julia> using Symbolics

julia> @variables t;

julia> U = DiscreteUpdate(t; dt=0.01)
(::Difference) (generic function with 2 methods)
```
