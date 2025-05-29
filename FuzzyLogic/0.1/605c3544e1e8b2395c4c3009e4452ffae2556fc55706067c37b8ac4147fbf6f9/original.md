```julia
struct ZShapeMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Z-shaped membership function.

### Fields

  * `a::Real`: shoulder.
  * `b::Real`: foot.

### Example

```julia
mf = ZShapeMF(3, 7)
```
