```julia
struct SShapeMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

S-shaped membership function.

### Fields

  * `a::Real`: foot.
  * `b::Real`: shoulder.

### Example

```julia
mf = SShapeMF(1, 8)
```
