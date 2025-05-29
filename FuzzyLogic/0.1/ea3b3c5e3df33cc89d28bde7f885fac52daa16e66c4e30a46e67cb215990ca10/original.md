```julia
struct TriangularMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Triangular membership function.

### Fields

  * `a::Real`: left foot.
  * `b::Real`: peak.
  * `c::Real`: right foot.

### Example

```julia
mf = TriangularMF(3, 5, 7)
```
