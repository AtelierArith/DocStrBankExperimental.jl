```julia
struct Shift <: Symbolics.Operator
```

Represents a shift operator.

# Fields

  * `t`: Fixed Shift
  * `steps`

# Examples

```jldoctest
julia> using Symbolics

julia> Δ = Shift(t)
(::Shift) (generic function with 2 methods)
```
