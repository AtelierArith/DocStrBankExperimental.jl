```julia
struct TrapezoidalMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Trapezoidal membership function.

### Fields

  * `a::Real`: left foot.
  * `b::Real`: left shoulder.
  * `c::Real`: right shoulder.
  * `d::Real`: right foot.

### Example

```julia
mf = TrapezoidalMF(1, 3, 7, 9)
```
