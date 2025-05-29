```julia
struct PiShapeMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Π-shaped membership function.

### Fields

  * `a::Real`: left foot.
  * `b::Real`: left shoulder.
  * `c::Real`: right shoulder.
  * `d::Real`: right foot.

### Example

```julia
mf = PiShapeMF(1, 4, 5, 10)
```
