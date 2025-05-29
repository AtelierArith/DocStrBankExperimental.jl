```julia
struct Difference <: Symbolics.Operator
```

Represents a difference operator.

# Fields

  * `t`: Fixed Difference
  * `dt`
  * `update`

# Examples

```jldoctest
julia> using Symbolics

julia> @variables t;

julia> Δ = Difference(t; dt=0.01)
(::Difference) (generic function with 2 methods)
```
